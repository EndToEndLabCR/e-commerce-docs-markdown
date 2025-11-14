# Technical Architecture - Electronics Store for Programmers

## Architecture Overview

The Electronics Store for Programmers follows Clean Architecture principles combined with Domain-Driven Design (DDD) tactical patterns to create a maintainable, testable, and scalable e-commerce platform.

### Architectural Principles

1. **Separation of Concerns**: Each layer has distinct responsibilities
2. **Dependency Inversion**: Dependencies point inward toward the domain
3. **Technology Independence**: Business logic is framework-agnostic
4. **Testability**: High test coverage through dependency injection
5. **Scalability**: Horizontal scaling capability with stateless services

---

## System Architecture Layers

### 1. Domain Layer (Core Business Logic)

**Purpose**: Contains enterprise business rules and domain logic independent of any framework or technology.

**Components**:

- **Entities**: User, Product, Order, Cart, Review, Discount, BlogPost
- **Value Objects**: Money, Email, Address, Password, ProductSpecification, Rating
- **Aggregates**: 
  - User (root) → Address collection
  - Product (root) → ProductImage collection, ProductSpecification collection
  - Order (root) → OrderItem entities, ShippingAddress, Payment
  - Cart (root) → CartItem entities
- **Domain Services**: PricingService, InventoryService, DiscountCalculator
- **Repository Interfaces**: IUserRepository, IProductRepository, IOrderRepository, ICartRepository
- **Domain Events**: UserRegistered, OrderPlaced, PaymentProcessed, ProductReviewed

**Key Characteristics**:
- Zero dependencies on external frameworks
- Pure Python classes with business logic
- Immutable value objects
- Aggregate boundaries enforce consistency

**Example**:
```python
# domain/aggregates/order.py
class Order(AggregateRoot):
    def __init__(self, order_id: OrderId, user_id: UserId, items: List[OrderItem]):
        self._order_id = order_id
        self._user_id = user_id
        self._items = items
        self._status = OrderStatus.PENDING
        self._total = self._calculate_total()
    
    def apply_discount(self, discount: Discount) -> None:
        if not discount.is_valid_for_order(self):
            raise InvalidDiscountError()
        self._discount = discount
        self._total = self._calculate_total()
    
    def mark_as_paid(self, payment: Payment) -> None:
        if self._status != OrderStatus.PENDING:
            raise InvalidOrderStateError()
        self._status = OrderStatus.PAID
        self._add_domain_event(OrderPlaced(self._order_id, self._user_id))
```

---

### 2. Application Layer (Use Cases)

**Purpose**: Orchestrates domain objects to fulfill application-specific business rules. Contains use cases that implement user stories.

**Components**:

- **Use Cases (Commands)**: 
  - User: RegisterUser, LoginUser, UpdateUserProfile, ResetPassword
  - Product: CreateProduct, UpdateProduct, DeleteProduct, GetProductList, SearchProducts
  - Cart: AddToCart, UpdateCartItem, RemoveFromCart, GetCart
  - Order: CreateOrder, ProcessPayment, GetOrderHistory, GetOrderDetails
  - Review: CreateReview, GetProductReviews
- **DTOs**: UserDTO, ProductDTO, OrderDTO, CartDTO (for API request/response)
- **Application Services**: UserService, ProductService, OrderService, CartService
- **Interfaces**: IEmailService, IPaymentService, IStorageService
- **Specifications**: ProductSpecification (for complex queries)

**Key Characteristics**:
- Thin orchestration layer
- Depends only on domain layer
- Defines interfaces for external services
- Returns DTOs, not domain entities

**Example**:
```python
# application/use_cases/create_order.py
class CreateOrderUseCase:
    def __init__(
        self,
        order_repository: IOrderRepository,
        cart_repository: ICartRepository,
        payment_service: IPaymentService,
        email_service: IEmailService
    ):
        self._order_repo = order_repository
        self._cart_repo = cart_repository
        self._payment_service = payment_service
        self._email_service = email_service
    
    async def execute(self, command: CreateOrderCommand) -> OrderDTO:
        cart = await self._cart_repo.get_by_user(command.user_id)
        order = Order.from_cart(cart, command.shipping_address)
        
        payment_result = await self._payment_service.process_payment(
            order.total, command.payment_method
        )
        
        if payment_result.is_success:
            order.mark_as_paid(payment_result.payment)
            await self._order_repo.save(order)
            await self._email_service.send_order_confirmation(order)
            return OrderDTO.from_entity(order)
        else:
            raise PaymentFailedError(payment_result.error_message)
```

---

### 3. Infrastructure Layer (Technical Implementation)

**Purpose**: Provides concrete implementations of interfaces defined in application layer. Contains framework-specific code.

**Components**:

- **Database**:
  - SQLAlchemy models (ORM mappings)
  - Repository implementations
  - Alembic migrations
  - Database connection pooling
  
- **External Services**:
  - Stripe payment service implementation
  - PayPal payment service implementation
  - SendGrid email service implementation
  - AWS S3 storage service implementation
  
- **Caching**:
  - Redis cache implementation
  - Cache decorators for repositories
  
- **Logging & Monitoring**:
  - Structured logging with Python logging
  - Prometheus metrics
  - Sentry error tracking

**Key Characteristics**:
- Implements application layer interfaces
- Contains all external dependencies
- Technology-specific implementations
- Easily replaceable (e.g., swap S3 for local storage in tests)

**Example**:
```python
# infrastructure/repositories/order_repository.py
class SqlAlchemyOrderRepository(IOrderRepository):
    def __init__(self, db_session: AsyncSession):
        self._session = db_session
    
    async def save(self, order: Order) -> None:
        order_model = OrderModel.from_entity(order)
        self._session.add(order_model)
        await self._session.commit()
    
    async def get_by_id(self, order_id: OrderId) -> Optional[Order]:
        result = await self._session.execute(
            select(OrderModel).where(OrderModel.id == order_id.value)
        )
        order_model = result.scalar_one_or_none()
        return order_model.to_entity() if order_model else None
```

---

### 4. Presentation Layer (API & UI)

**Purpose**: Handles HTTP requests, authentication, validation, and response formatting. Entry point for all external interactions.

**Components**:

**Backend (FastAPI)**:
- REST API endpoints (routers)
- Request/response models (Pydantic)
- Authentication middleware (JWT)
- Input validation
- Error handling
- OpenAPI/Swagger documentation
- Rate limiting
- CORS configuration

**Frontend (React)**:
- React components (pages, UI components)
- Redux Toolkit store (state management)
- API client (Axios)
- React Router (navigation)
- Form handling and validation
- Error boundaries

**Key Characteristics**:
- Thin layer that delegates to application services
- Converts between HTTP and application DTOs
- Handles cross-cutting concerns (auth, logging, rate limiting)
- No business logic

**Backend Example**:
```python
# presentation/api/routers/orders.py
@router.post("/orders", response_model=OrderResponse, status_code=201)
async def create_order(
    order_request: CreateOrderRequest,
    current_user: User = Depends(get_current_user),
    order_service: OrderService = Depends(get_order_service)
):
    command = CreateOrderCommand(
        user_id=current_user.id,
        shipping_address=order_request.shipping_address,
        payment_method=order_request.payment_method
    )
    order_dto = await order_service.create_order(command)
    return OrderResponse.from_dto(order_dto)
```

**Frontend Example**:
```typescript
// presentation/frontend/src/features/cart/cartSlice.ts
export const addToCart = createAsyncThunk(
  'cart/addItem',
  async (productId: string, { getState, rejectWithValue }) => {
    try {
      const response = await api.post('/cart/items', { product_id: productId });
      return response.data;
    } catch (error) {
      return rejectWithValue(error.response.data);
    }
  }
);
```

---

## Domain-Driven Design Patterns

### Bounded Contexts

The system is divided into several bounded contexts:

1. **UserManagement Context**
   - User authentication and authorization
   - Profile management
   - Role-based access control

2. **ProductCatalog Context**
   - Product management
   - Category hierarchy
   - Product search and filtering

3. **ShoppingCart Context**
   - Cart management
   - Cart persistence

4. **OrderManagement Context**
   - Order creation and processing
   - Order history
   - Returns and cancellations

5. **PaymentProcessing Context**
   - Payment integration
   - Refund processing
   - Payment method management

6. **ContentManagement Context**
   - Blog posts
   - SEO metadata

7. **CustomerSupport Context**
   - Reviews and ratings
   - Live chat integration

### Entities vs Value Objects

**Entities** (have identity, mutable):
- User (identified by UserId)
- Product (identified by ProductId)
- Order (identified by OrderId)
- Cart (identified by CartId)
- Review (identified by ReviewId)

**Value Objects** (no identity, immutable):
- Money (amount, currency)
- Email (value, validated)
- Address (street, city, state, postal_code, country)
- ProductSpecification (key, value, unit)
- Rating (value 1-5)

### Aggregate Boundaries

**User Aggregate**:
- Root: User
- Entities: None
- Value Objects: Email, Password (hashed), Address collection
- Invariants: Email uniqueness, password strength

**Product Aggregate**:
- Root: Product
- Entities: None
- Value Objects: Money (price), ProductSpecification collection, ProductImage collection
- Invariants: Price must be positive, SKU uniqueness

**Order Aggregate**:
- Root: Order
- Entities: OrderItem (part of aggregate)
- Value Objects: Money (total), Address (shipping), Payment
- Invariants: Order total = sum of line items minus discount, order can only be modified before payment

**Cart Aggregate**:
- Root: Cart
- Entities: CartItem (part of aggregate)
- Value Objects: Money (total)
- Invariants: Cart belongs to one user, quantities must be positive

---

## Technology Stack Details

### Backend Technologies

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| Web Framework | FastAPI | 0.104+ | REST API, async support, automatic OpenAPI docs |
| Language | Python | 3.11+ | Type hints, performance, async/await |
| Database | PostgreSQL | 15+ | Relational data, ACID compliance, full-text search |
| ORM | SQLAlchemy | 2.0+ | Database abstraction, async support, migrations |
| Migration Tool | Alembic | Latest | Database schema versioning |
| Authentication | JWT | via python-jose | Stateless authentication tokens |
| Validation | Pydantic | 2.0+ | Request/response validation, settings management |
| Testing | Pytest | Latest | Unit and integration tests |
| Async Testing | pytest-asyncio | Latest | Async test support |
| Caching | Redis | 7+ | Session storage, query caching, rate limiting |
| Task Queue | Celery (future) | Latest | Background jobs (email, analytics) |
| Payment | Stripe SDK | Latest | Payment processing |
| Payment (Alt) | PayPal SDK | Latest | Alternative payment method |
| Email | SendGrid | via sendgrid | Transactional emails |
| Storage | AWS S3 | boto3 | Product images, user uploads |

### Frontend Technologies

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| Framework | React | 18 | Component-based UI |
| Language | TypeScript | 5+ | Type safety, better DX |
| Build Tool | Vite | 5+ | Fast builds, HMR, optimization |
| UI Library | Ant Design | 5+ | Pre-built components, design system |
| State Management | Redux Toolkit | Latest | Centralized state, async actions |
| Routing | React Router | 6 | Client-side routing, nested routes |
| API Client | Axios | Latest | HTTP requests, interceptors |
| Form Handling | React Hook Form | Latest | Performance, validation |
| Validation | Zod | Latest | Schema validation |
| Styling | CSS Modules + SCSS | Latest | Scoped styles, variables |
| Testing | Jest | Latest | Unit and integration tests |
| Testing (React) | React Testing Library | Latest | Component testing |
| Icons | Ant Design Icons | Latest | Consistent iconography |

### Infrastructure & DevOps

| Component | Technology | Purpose |
|-----------|-----------|---------|
| CI/CD | GitHub Actions | Automated testing, deployment |
| Containerization | Docker | Development and production environments |
| Orchestration | Docker Compose | Local development |
| Cloud Provider | AWS | Infrastructure hosting |
| Compute | EC2 / ECS | Application servers |
| Database | RDS (PostgreSQL) | Managed database |
| Object Storage | S3 | Static assets, images |
| CDN | CloudFront | Content delivery, caching |
| Cache | ElastiCache (Redis) | Managed Redis cluster |
| Monitoring | Prometheus + Grafana | Metrics and dashboards |
| Logging | ELK Stack | Centralized logging |
| Error Tracking | Sentry | Error monitoring, alerting |
| SSL/TLS | Let's Encrypt / ACM | HTTPS certificates |

---

## Database Schema (High-Level)

### Core Tables

**users**
- id (UUID, PK)
- email (VARCHAR, unique)
- password_hash (VARCHAR)
- first_name (VARCHAR)
- last_name (VARCHAR)
- role (ENUM: customer, admin)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)

**products**
- id (UUID, PK)
- name (VARCHAR)
- description (TEXT)
- sku (VARCHAR, unique)
- price_amount (DECIMAL)
- price_currency (VARCHAR)
- category_id (UUID, FK)
- stock_quantity (INTEGER)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)

**orders**
- id (UUID, PK)
- user_id (UUID, FK)
- status (ENUM: pending, paid, shipped, delivered, cancelled)
- subtotal_amount (DECIMAL)
- discount_amount (DECIMAL)
- total_amount (DECIMAL)
- shipping_address_id (UUID, FK)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)

**order_items**
- id (UUID, PK)
- order_id (UUID, FK)
- product_id (UUID, FK)
- quantity (INTEGER)
- unit_price_amount (DECIMAL)
- subtotal_amount (DECIMAL)

**carts**
- id (UUID, PK)
- user_id (UUID, FK, unique)
- created_at (TIMESTAMP)
- updated_at (TIMESTAMP)

**cart_items**
- id (UUID, PK)
- cart_id (UUID, FK)
- product_id (UUID, FK)
- quantity (INTEGER)

**reviews**
- id (UUID, PK)
- product_id (UUID, FK)
- user_id (UUID, FK)
- rating (INTEGER, 1-5)
- text (TEXT)
- verified_purchase (BOOLEAN)
- created_at (TIMESTAMP)

### Additional Tables

- addresses
- categories
- product_images
- product_specifications
- discounts
- blog_posts
- wishlists
- wishlist_items
- payments

---

## API Design

### RESTful Conventions

- **Resources**: Nouns (plural) for endpoints (e.g., `/products`, `/orders`)
- **HTTP Methods**: GET (read), POST (create), PUT/PATCH (update), DELETE (delete)
- **Status Codes**: 200 (OK), 201 (Created), 204 (No Content), 400 (Bad Request), 401 (Unauthorized), 403 (Forbidden), 404 (Not Found), 500 (Internal Server Error)
- **Pagination**: Query parameters `?page=1&per_page=24`
- **Filtering**: Query parameters `?category=keyboards&price_min=50&price_max=200`
- **Sorting**: Query parameter `?sort=price_asc` or `?sort=rating_desc`

### Example Endpoints

```
# Authentication
POST   /api/v1/auth/register
POST   /api/v1/auth/login
POST   /api/v1/auth/logout
POST   /api/v1/auth/refresh
POST   /api/v1/auth/password-reset-request
POST   /api/v1/auth/password-reset

# Products
GET    /api/v1/products                 # List with pagination/filtering
GET    /api/v1/products/{id}            # Get details
GET    /api/v1/products/{id}/reviews    # Get product reviews
POST   /api/v1/products                 # Admin: Create product
PUT    /api/v1/products/{id}            # Admin: Update product
DELETE /api/v1/products/{id}            # Admin: Delete product

# Cart
GET    /api/v1/cart                     # Get current user's cart
POST   /api/v1/cart/items               # Add item to cart
PATCH  /api/v1/cart/items/{id}          # Update quantity
DELETE /api/v1/cart/items/{id}          # Remove from cart

# Orders
GET    /api/v1/orders                   # Get user's order history
GET    /api/v1/orders/{id}              # Get order details
POST   /api/v1/orders                   # Create order (checkout)

# Wishlist
GET    /api/v1/wishlist                 # Get wishlist
POST   /api/v1/wishlist/items           # Add to wishlist
DELETE /api/v1/wishlist/items/{id}      # Remove from wishlist

# Reviews
POST   /api/v1/reviews                  # Create review
GET    /api/v1/reviews/{id}             # Get review details

# Admin
GET    /api/v1/admin/products           # List all products
GET    /api/v1/admin/orders             # List all orders
PATCH  /api/v1/admin/orders/{id}/status # Update order status
GET    /api/v1/admin/analytics          # Get analytics data
```

---

## Security Architecture

### Authentication & Authorization

- **JWT Tokens**: Stateless authentication with access tokens (24h expiration)
- **Refresh Tokens** (Phase 2): Long-lived tokens for obtaining new access tokens
- **Password Security**: bcrypt hashing with cost factor 12
- **Role-Based Access Control (RBAC)**: User roles (customer, admin) enforced at API level

### Data Security

- **Input Validation**: Pydantic models validate all API inputs
- **SQL Injection Prevention**: SQLAlchemy parameterized queries
- **XSS Prevention**: React automatic escaping, CSP headers
- **CSRF Protection**: CSRF tokens for state-changing operations (cookies)
- **HTTPS Enforcement**: TLS 1.3, HSTS headers
- **Secure Cookies**: httpOnly, secure, sameSite flags for auth cookies

### Rate Limiting

- **Authentication endpoints**: 5 requests per 15 minutes per IP
- **API endpoints**: 100 requests per minute per user
- **Admin endpoints**: 200 requests per minute per admin

### Payment Security

- **PCI DSS Compliance**: Using Stripe/PayPal (card data never touches our servers)
- **Payment Idempotency**: Prevent double-charging with idempotency keys
- **Fraud Detection**: Stripe Radar for fraud prevention

---

## Performance & Scalability

### Caching Strategy

- **Redis Caching**:
  - Product catalog (5-minute TTL)
  - User sessions (24-hour TTL)
  - API response caching for frequently accessed data
  - Rate limiting counters

### Database Optimization

- **Indexes**: On foreign keys, frequently queried fields (email, SKU, category_id)
- **Connection Pooling**: SQLAlchemy async connection pool (min 5, max 20)
- **Query Optimization**: Eager loading for relationships, avoid N+1 queries
- **Read Replicas** (future): For analytics and reporting queries

### Frontend Optimization

- **Code Splitting**: React lazy loading for routes
- **Image Optimization**: Responsive images, WebP format, lazy loading
- **CDN**: CloudFront for static assets
- **Bundle Optimization**: Vite tree-shaking, minification

### Horizontal Scaling

- **Stateless API**: No session state in application servers
- **Load Balancer**: AWS ALB distributing traffic across multiple EC2 instances
- **Database**: Vertical scaling initially, read replicas for future growth
- **Cache**: Redis cluster for high availability

---

**Document Owner**: Tech Lead  
**Contributors**: Backend Engineer, Frontend Engineer  
**Last Updated**: November 12, 2025  
**Version**: 1.0.0  
**Status**: ✅ Approved - Implementation Guide
