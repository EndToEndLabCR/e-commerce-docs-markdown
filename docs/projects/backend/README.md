# Electronics Store - Backend API

FastAPI-based backend for the Electronics Store for Programmers e-commerce platform, following Clean Architecture and Domain-Driven Design principles.

## Technology Stack

- **Framework**: FastAPI 0.104+
- **Language**: Python 3.11+
- **Database**: PostgreSQL 15+
- **ORM**: SQLAlchemy 2.0+ (async)
- **Migrations**: Alembic
- **Authentication**: JWT (python-jose)
- **Validation**: Pydantic 2.0+
- **Testing**: Pytest + pytest-asyncio
- **Caching**: Redis 7+
- **Payments**: Stripe SDK, PayPal SDK
- **Email**: SendGrid
- **Storage**: AWS S3 (boto3)

## Project Structure

```
backend/
├── src/
│   ├── domain/              # Domain layer (entities, value objects, aggregates)
│   │   ├── aggregates/
│   │   │   ├── user.py
│   │   │   ├── product.py
│   │   │   ├── order.py
│   │   │   └── cart.py
│   │   ├── value_objects/
│   │   │   ├── money.py
│   │   │   ├── email.py
│   │   │   └── address.py
│   │   ├── repositories/    # Repository interfaces
│   │   └── events/          # Domain events
│   ├── application/         # Application layer (use cases, DTOs, interfaces)
│   │   ├── use_cases/
│   │   ├── dtos/
│   │   ├── interfaces/
│   │   └── services/
│   ├── infrastructure/      # Infrastructure layer (implementations)
│   │   ├── database/
│   │   │   ├── models/      # SQLAlchemy models
│   │   │   └── repositories/ # Repository implementations
│   │   ├── external_services/
│   │   │   ├── stripe_service.py
│   │   │   ├── email_service.py
│   │   │   └── storage_service.py
│   │   └── cache/
│   ├── presentation/        # Presentation layer (FastAPI routes, middleware)
│   │   ├── api/
│   │   │   ├── routers/
│   │   │   ├── middleware/
│   │   │   └── dependencies.py
│   │   └── schemas/         # Pydantic request/response schemas
│   ├── config.py            # Configuration management
│   └── main.py              # FastAPI application entry point
├── tests/
│   ├── unit/
│   ├── integration/
│   └── conftest.py
├── alembic/                 # Database migrations
├── requirements.txt
├── requirements-dev.txt
├── .env.example
├── .gitignore
├── Dockerfile
├── docker-compose.yml
└── README.md
```

## Prerequisites

- Python 3.11 or higher
- PostgreSQL 15 or higher
- Redis 7 or higher
- AWS account (for S3)
- Stripe account (for payments)
- SendGrid account (for email)

## Setup Instructions

### 1. Clone Repository
```bash
git clone <repository-url>
cd electronics-store/backend
```

### 2. Create Virtual Environment
```bash
python3.11 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
pip install -r requirements-dev.txt  # For development
```

### 4. Configure Environment Variables
```bash
cp .env.example .env
# Edit .env with your configuration
```

Required environment variables:
```env
# Database
DATABASE_URL=postgresql+asyncpg://user:password@localhost:5432/electronics_store
TEST_DATABASE_URL=postgresql+asyncpg://user:password@localhost:5432/electronics_store_test

# Redis
REDIS_URL=redis://localhost:6379/0

# JWT
SECRET_KEY=your-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# Email (SendGrid)
SENDGRID_API_KEY=your-sendgrid-api-key
FROM_EMAIL=noreply@electronicsstore.com

# Stripe
STRIPE_API_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...

# PayPal (Phase 1)
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret

# AWS S3
AWS_ACCESS_KEY_ID=your-access-key
AWS_SECRET_ACCESS_KEY=your-secret-key
S3_BUCKET_NAME=electronics-store-images
AWS_REGION=us-east-1

# Environment
ENVIRONMENT=development  # development, staging, production
```

### 5. Set Up Database
```bash
# Start PostgreSQL (if using Docker)
docker-compose up -d postgres

# Run migrations
alembic upgrade head
```

### 6. Seed Database (Optional)
```bash
python scripts/seed_data.py
```

### 7. Run Development Server
```bash
uvicorn src.main:app --reload --port 8000
```

API will be available at http://localhost:8000  
OpenAPI docs at http://localhost:8000/docs

## Running Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src --cov-report=html

# Run specific test file
pytest tests/unit/domain/test_user.py

# Run with verbose output
pytest -v
```

## Code Quality

### Linting
```bash
# Run Black formatter
black src tests

# Run Flake8
flake8 src tests

# Run MyPy (type checking)
mypy src
```

### Pre-commit Hooks
```bash
# Install pre-commit hooks
pre-commit install

# Run manually
pre-commit run --all-files
```

## Database Migrations

### Create Migration
```bash
alembic revision --autogenerate -m "Description of changes"
```

### Apply Migrations
```bash
alembic upgrade head
```

### Rollback Migration
```bash
alembic downgrade -1
```

## Docker

### Build Image
```bash
docker build -t electronics-store-backend .
```

### Run with Docker Compose
```bash
docker-compose up
```

## API Documentation

- **OpenAPI/Swagger**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

## Development Guidelines

### Clean Architecture Principles
- Domain layer has no dependencies on other layers
- Application layer depends only on domain
- Infrastructure implements interfaces from application layer
- Presentation layer is thin, delegates to application services

### Coding Standards
- Follow PEP 8 style guide
- Use type hints for all functions
- Write docstrings for public APIs
- Keep functions small and focused (< 20 lines)
- Use meaningful variable and function names

### Testing Standards
- Write tests for all business logic (domain & application layers)
- Target 85%+ code coverage for domain/application
- Target 70%+ code coverage for infrastructure/presentation
- Use fixtures for common test data
- Mock external services in tests

### Git Workflow
- Create feature branch from `main`
- Make small, focused commits
- Write clear commit messages (Conventional Commits)
- Create PR with description and linked issue
- Ensure all tests pass and linting is clean
- Get code review approval before merging

## Troubleshooting

### Database Connection Errors
- Ensure PostgreSQL is running
- Check DATABASE_URL in .env
- Verify database credentials

### Import Errors
- Ensure virtual environment is activated
- Run `pip install -r requirements.txt`

### Test Failures
- Check TEST_DATABASE_URL configuration
- Ensure test database exists and is clean
- Run `alembic upgrade head` on test database

## Additional Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)
- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Domain-Driven Design](https://martinfowler.com/tags/domain%20driven%20design.html)

---

**Maintainers**: Backend Engineering Team  
**Last Updated**: November 12, 2025
