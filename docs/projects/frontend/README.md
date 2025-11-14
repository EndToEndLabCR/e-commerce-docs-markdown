# Electronics Store - Frontend Application

Modern, responsive React application for the Electronics Store for Programmers e-commerce platform.

## Technology Stack

- **Framework**: React 18
- **Language**: TypeScript 5+
- **Build Tool**: Vite 5+
- **UI Library**: Ant Design 5+
- **State Management**: Redux Toolkit
- **Routing**: React Router 6
- **API Client**: Axios
- **Form Handling**: React Hook Form + Zod
- **Styling**: CSS Modules + SCSS
- **Testing**: Vitest + React Testing Library

## Project Structure

```
frontend/
├── src/
│   ├── app/                 # App setup and configuration
│   │   ├── store.ts        # Redux store
│   │   └── App.tsx         # Root component
│   ├── features/            # Feature-based modules
│   │   ├── auth/
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   ├── slices/     # Redux slices
│   │   │   └── types/
│   │   ├── products/
│   │   ├── cart/
│   │   ├── checkout/
│   │   ├── orders/
│   │   └── admin/
│   ├── shared/              # Shared components and utilities
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── types/
│   │   └── utils/
│   ├── assets/              # Static assets (images, fonts)
│   ├── styles/              # Global styles
│   ├── config/              # App configuration
│   ├── main.tsx            # Entry point
│   └── vite-env.d.ts
├── public/                  # Public static files
├── tests/
│   ├── unit/
│   ├── integration/
│   └── setup.ts
├── .env.example
├── .gitignore
├── package.json
├── tsconfig.json
├── vite.config.ts
├── eslint.config.js
├── .prettierrc
└── README.md
```

## Prerequisites

- Node.js 18+ LTS
- npm or yarn
- Backend API running (or configured API URL)

## Setup Instructions

### 1. Clone Repository
```bash
git clone <repository-url>
cd electronics-store/frontend
```

### 2. Install Dependencies
```bash
npm install
# or
yarn install
```

### 3. Configure Environment Variables
```bash
cp .env.example .env
# Edit .env with your configuration
```

Required environment variables:
```env
VITE_API_BASE_URL=http://localhost:8000/api/v1
VITE_STRIPE_PUBLISHABLE_KEY=pk_test_...
VITE_GOOGLE_ANALYTICS_ID=G-XXXXXXXXXX
VITE_ENVIRONMENT=development
```

### 4. Run Development Server
```bash
npm run dev
# or
yarn dev
```

Application will be available at http://localhost:5173

## Available Scripts

### Development
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build locally
npm run lint         # Run ESLint
npm run format       # Format code with Prettier
npm run type-check   # Run TypeScript type checking
```

### Testing
```bash
npm run test         # Run tests
npm run test:ui      # Run tests with UI
npm run test:coverage # Run tests with coverage report
```

## Building for Production

```bash
# Build optimized production bundle
npm run build

# Preview production build
npm run preview
```

Build output will be in the `dist/` directory.

## Code Quality

### Linting
```bash
# Run ESLint
npm run lint

# Fix auto-fixable issues
npm run lint:fix
```

### Formatting
```bash
# Check formatting
npm run format:check

# Format all files
npm run format
```

### Type Checking
```bash
# Check TypeScript types
npm run type-check
```

## Project Guidelines

### Component Organization
- Use functional components with hooks
- Extract reusable logic into custom hooks
- Keep components small and focused (< 200 lines)
- Use TypeScript for all components and utilities

### State Management
- Use Redux Toolkit for global state
- Use local state (useState) for component-specific state
- Use React Query for server state (future enhancement)
- Avoid prop drilling (use context or Redux)

### Styling
- Use CSS Modules for component-specific styles
- Use SCSS for variables and mixins
- Follow Ant Design design tokens
- Ensure responsive design (mobile-first)

### API Integration
- Use Axios for HTTP requests
- Create API service files in features/[feature]/services
- Use TypeScript types for request/response
- Handle errors consistently

### Form Handling
- Use React Hook Form for forms
- Use Zod for validation schemas
- Provide clear error messages
- Validate on blur and submit

### Testing
- Write tests for all components and utilities
- Target 70%+ code coverage
- Use React Testing Library best practices
- Mock API calls in tests

### Accessibility
- Use semantic HTML elements
- Provide ARIA labels where needed
- Ensure keyboard navigation works
- Test with screen readers
- Maintain 4.5:1 color contrast ratio

## Development Workflow

### Creating a New Feature
1. Create feature directory in `src/features/`
2. Add components, services, slices, types
3. Create tests for each component
4. Update routing if needed
5. Add to navigation if applicable

### Adding a New Route
```typescript
// src/app/routes.tsx
import { Route } from 'react-router-dom';
import NewFeature from '@/features/newFeature/pages/NewFeature';

<Route path="/new-feature" element={<NewFeature />} />
```

### Creating a Redux Slice
```typescript
// src/features/[feature]/slices/[feature]Slice.ts
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchData = createAsyncThunk(
  'feature/fetchData',
  async () => {
    const response = await api.get('/endpoint');
    return response.data;
  }
);

const featureSlice = createSlice({
  name: 'feature',
  initialState,
  reducers: {},
  extraReducers: (builder) => {
    builder.addCase(fetchData.fulfilled, (state, action) => {
      // Update state
    });
  }
});
```

## Troubleshooting

### Build Errors
- Clear node_modules and reinstall: `rm -rf node_modules && npm install`
- Clear Vite cache: `rm -rf node_modules/.vite`
- Check for TypeScript errors: `npm run type-check`

### API Connection Issues
- Verify VITE_API_BASE_URL in .env
- Ensure backend is running
- Check CORS configuration on backend

### Styling Issues
- Clear browser cache
- Check CSS module imports
- Verify Ant Design theme configuration

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Performance Optimization

- Code splitting with React.lazy
- Image lazy loading
- Memoization with React.memo and useMemo
- Virtual scrolling for large lists
- Bundle size optimization with tree-shaking

## Additional Resources

- [React Documentation](https://react.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [Vite Documentation](https://vitejs.dev/)
- [Ant Design Documentation](https://ant.design/)
- [Redux Toolkit Documentation](https://redux-toolkit.js.org/)

---

**Maintainers**: Frontend Engineering Team  
**Last Updated**: November 12, 2025
