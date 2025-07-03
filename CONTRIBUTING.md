
# 🤝 Contributing to ShopLinker

Thank you for your interest in contributing to ShopLinker! This guide will help you get started with contributing to our multivendor marketplace platform.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Issue Reporting](#issue-reporting)

## 📜 Code of Conduct

### Our Pledge

We are committed to making participation in our project a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

### Our Standards

Examples of behavior that contributes to creating a positive environment include:

- Using welcoming and inclusive language
- Being respectful of differing viewpoints and experiences
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

## 🚀 Getting Started

### Prerequisites

- Node.js 18 or higher
- PostgreSQL database
- Git
- Code editor (VS Code recommended)

### Development Setup

1. **Fork the repository**
   ```bash
   git clone https://github.com/your-username/shoplinker.git
   cd shoplinker/app
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your database credentials
   ```

4. **Set up the database**
   ```bash
   npx prisma generate
   npx prisma db push
   npx prisma db seed
   ```

5. **Start development server**
   ```bash
   npm run dev
   ```

## 🔄 Development Workflow

### Branch Naming Convention

- `feature/feature-name` - New features
- `bugfix/bug-description` - Bug fixes
- `hotfix/critical-fix` - Critical production fixes
- `docs/documentation-update` - Documentation updates
- `refactor/component-name` - Code refactoring

### Commit Message Format

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Types:**
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to the build process or auxiliary tools

**Examples:**
```bash
feat(auth): add social login with Google
fix(cart): resolve quantity update issue
docs(api): update authentication endpoints
refactor(components): extract reusable button component
```

## 🔀 Pull Request Process

### Before Submitting

1. **Update your fork**
   ```bash
   git checkout main
   git pull upstream main
   git checkout your-feature-branch
   git rebase main
   ```

2. **Run tests**
   ```bash
   npm run test
   npm run lint
   npm run type-check
   ```

3. **Build the project**
   ```bash
   npm run build
   ```

### Pull Request Template

When creating a pull request, please include:

```markdown
## Description
Brief description of the changes made.

## Type of Change
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

## Testing
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing unit tests pass locally with my changes
- [ ] I have tested this change in a browser

## Screenshots (if applicable)
Add screenshots to help explain your changes.

## Checklist
- [ ] My code follows the style guidelines of this project
- [ ] I have performed a self-review of my own code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
```

### Review Process

1. **Automated Checks**: All PRs must pass automated tests and linting
2. **Code Review**: At least one maintainer must review and approve
3. **Testing**: Changes should be tested in development environment
4. **Documentation**: Update relevant documentation if needed

## 📝 Coding Standards

### TypeScript Guidelines

- Use TypeScript for all new code
- Define proper interfaces and types
- Avoid `any` type unless absolutely necessary
- Use strict mode settings

```typescript
// Good
interface Product {
  id: string;
  name: string;
  price: number;
  vendor: Vendor;
}

// Avoid
const product: any = { ... };
```

### React Component Guidelines

- Use functional components with hooks
- Follow the single responsibility principle
- Use proper prop types and interfaces
- Implement proper error boundaries

```typescript
// Good
interface ProductCardProps {
  product: Product;
  onAddToCart: (productId: string) => void;
}

export function ProductCard({ product, onAddToCart }: ProductCardProps) {
  // Component implementation
}
```

### CSS/Styling Guidelines

- Use Tailwind CSS utility classes
- Follow mobile-first responsive design
- Use semantic class names for custom CSS
- Maintain consistent spacing and typography

```tsx
// Good
<div className="flex flex-col space-y-4 p-6 bg-white rounded-lg shadow-md">
  <h2 className="text-xl font-semibold text-gray-900">{product.name}</h2>
  <p className="text-gray-600">{product.description}</p>
</div>
```

### API Guidelines

- Use RESTful conventions
- Implement proper error handling
- Include input validation
- Return consistent response formats

```typescript
// Good
export async function POST(request: Request) {
  try {
    const body = await request.json();
    const validatedData = productSchema.parse(body);
    
    const product = await createProduct(validatedData);
    
    return NextResponse.json({ product }, { status: 201 });
  } catch (error) {
    if (error instanceof ZodError) {
      return NextResponse.json(
        { error: 'Validation failed', details: error.errors },
        { status: 400 }
      );
    }
    
    return NextResponse.json(
      { error: 'Internal server error' },
      { status: 500 }
    );
  }
}
```

## 🧪 Testing Guidelines

### Unit Tests

- Write tests for all utility functions
- Test React components with React Testing Library
- Aim for at least 80% code coverage

```typescript
// Example test
import { render, screen } from '@testing-library/react';
import { ProductCard } from './ProductCard';

describe('ProductCard', () => {
  const mockProduct = {
    id: '1',
    name: 'Test Product',
    price: 99.99,
    // ... other properties
  };

  it('displays product name and price', () => {
    render(<ProductCard product={mockProduct} onAddToCart={jest.fn()} />);
    
    expect(screen.getByText('Test Product')).toBeInTheDocument();
    expect(screen.getByText('$99.99')).toBeInTheDocument();
  });
});
```

### Integration Tests

- Test API endpoints with proper setup/teardown
- Use test database for integration tests
- Test complete user workflows

### E2E Tests

- Test critical user journeys
- Use Playwright or Cypress for E2E testing
- Run E2E tests in CI/CD pipeline

## 🐛 Issue Reporting

### Bug Reports

When reporting bugs, please include:

1. **Environment Information**
   - Operating System
   - Browser and version
   - Node.js version
   - Database version

2. **Steps to Reproduce**
   - Clear, numbered steps
   - Expected behavior
   - Actual behavior

3. **Additional Context**
   - Screenshots or videos
   - Error messages
   - Console logs

### Feature Requests

When requesting features, please include:

1. **Problem Description**
   - What problem does this solve?
   - Who would benefit from this feature?

2. **Proposed Solution**
   - Detailed description of the feature
   - How should it work?

3. **Alternatives Considered**
   - Other solutions you've considered
   - Why this approach is preferred

## 🏷️ Issue Labels

We use the following labels to categorize issues:

- `bug` - Something isn't working
- `enhancement` - New feature or request
- `documentation` - Improvements or additions to documentation
- `good first issue` - Good for newcomers
- `help wanted` - Extra attention is needed
- `priority: high` - High priority issue
- `priority: medium` - Medium priority issue
- `priority: low` - Low priority issue

## 🎯 Areas for Contribution

We welcome contributions in the following areas:

### 🔧 Technical Improvements

- Performance optimizations
- Security enhancements
- Code refactoring
- Test coverage improvements
- Accessibility improvements

### 🎨 UI/UX Enhancements

- Design improvements
- Mobile responsiveness
- User experience optimizations
- Animation and interactions

### 📚 Documentation

- API documentation
- User guides
- Developer tutorials
- Code comments

### 🌐 Internationalization

- Translation support
- Multi-language content
- Locale-specific features

### 🔌 Integrations

- Payment gateways
- Shipping providers
- Analytics tools
- Third-party services

## 🏆 Recognition

Contributors will be recognized in the following ways:

- Listed in the project's contributors section
- Mentioned in release notes for significant contributions
- Invited to join the core team for outstanding contributions

## 📞 Getting Help

If you need help with contributing:

- Join our Discord community
- Open a discussion on GitHub
- Reach out to maintainers
- Check existing documentation

## 📄 License

By contributing to ShopLinker, you agree that your contributions will be licensed under the same license as the project (MIT License).

---

Thank you for contributing to ShopLinker! Your efforts help make this project better for everyone. 🙏
