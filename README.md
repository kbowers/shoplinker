
# 🛒 ShopLinker - Multivendor Marketplace

[![Next.js](https://img.shields.io/badge/Next.js-14.2.28-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.2.2-blue?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3.3-38B2AC?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)
[![Prisma](https://img.shields.io/badge/Prisma-6.7.0-2D3748?style=flat-square&logo=prisma)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-336791?style=flat-square&logo=postgresql)](https://www.postgresql.org/)

A fully functional multivendor marketplace built with modern web technologies. ShopLinker enables multiple vendors to sell their products through a unified platform with comprehensive management tools for customers, vendors, and administrators.

## 🌟 Key Features

### 🔐 Multi-Role Authentication System
- **Customer Accounts**: Browse, purchase, and review products
- **Vendor Accounts**: Manage storefronts, products, and orders
- **Admin Panel**: Oversee the entire marketplace ecosystem
- Secure authentication powered by NextAuth.js

### 🏪 Vendor Storefronts
- **Subdirectory Routing**: Each vendor gets their own storefront (e.g., `/tech-haven`)
- **Customizable Profiles**: Logo, banner, description, and contact information
- **Vendor Analytics**: Sales tracking, commission reports, and performance metrics
- **Product Management**: Full CRUD operations for vendor products

### 📦 Product Management
- **Rich Product Listings**: Multiple images, detailed descriptions, and specifications
- **Category Organization**: Hierarchical category system
- **Inventory Tracking**: Stock levels, low stock alerts, and SKU management
- **SEO Optimization**: Meta titles, descriptions, and URL slugs

### 🛍️ Shopping Experience
- **Advanced Search & Filtering**: Find products by category, price, vendor, and more
- **Shopping Cart**: Persistent cart with quantity management
- **Secure Checkout**: Streamlined checkout process with address management
- **Order Tracking**: Real-time order status updates

### ⭐ Review & Rating System
- **Product Reviews**: Customers can rate and review purchased products
- **Verified Purchases**: Reviews marked as verified for authenticity
- **Helpful Votes**: Community-driven review quality assessment

### 📊 Analytics & Reporting
- **Vendor Dashboard**: Sales analytics, order management, and performance insights
- **Admin Analytics**: Platform-wide statistics and vendor performance
- **Commission Tracking**: Automated commission calculations and payouts

### 💳 Order Management
- **Multi-Status Tracking**: From pending to delivered with detailed status updates
- **Commission System**: Automated vendor commission calculations
- **Payment Integration**: Ready for payment gateway integration

## 🚀 Demo Accounts

### Customer Account
- **Email**: `john@doe.com`
- **Password**: `johndoe123`
- **Features**: Browse products, add to cart, place orders, write reviews

### Vendor Account
- **Email**: `vendor@demo.com`
- **Password**: `vendor123`
- **Store**: Tech Haven (`/tech-haven`)
- **Features**: Manage products, view orders, track sales analytics

### Admin Account
- **Email**: `admin@shoplinker.com`
- **Password**: `admin123`
- **Features**: Manage vendors, oversee orders, platform analytics

## 🏪 Demo Stores

### 1. Tech Haven (`/tech-haven`)
- **Specialty**: Electronics and gadgets
- **Products**: Wireless headphones, security cameras, portable chargers
- **Vendor**: Sarah Wilson (vendor@demo.com)

### 2. Artisan Craft Works (`/artisan-craft-works`)
- **Specialty**: Handmade crafts and home goods
- **Products**: Handwoven blankets, ceramic mugs, wooden cutting boards
- **Vendor**: Mike Chen (mike@craftworks.com)

### 3. Pure Naturals (`/pure-naturals`)
- **Specialty**: Organic beauty and personal care
- **Products**: Face moisturizers, natural shampoo sets
- **Vendor**: Emily Rodriguez (emily@naturals.com)

## 🎯 Feature Walkthrough

### For Customers
1. **Browse Products**: Visit the homepage and explore featured products
2. **Search & Filter**: Use the search bar or browse by categories
3. **Product Details**: Click on any product to view detailed information and reviews
4. **Add to Cart**: Add products to your cart and proceed to checkout
5. **Account Management**: Create an account to track orders and write reviews

### For Vendors
1. **Vendor Dashboard**: Access comprehensive analytics and order management
2. **Product Management**: Add, edit, and manage your product catalog
3. **Order Processing**: View and update order statuses
4. **Store Customization**: Update your store profile, logo, and banner
5. **Analytics**: Track sales performance and commission earnings

### For Administrators
1. **Platform Overview**: Monitor marketplace-wide statistics
2. **Vendor Management**: Approve new vendors and manage existing ones
3. **Order Oversight**: View all orders across the platform
4. **Category Management**: Organize and maintain product categories
5. **Commission Tracking**: Monitor and manage vendor commissions

## 🛠️ Technology Stack

### Frontend
- **Next.js 14.2.28**: React framework with App Router
- **TypeScript**: Type-safe development
- **Tailwind CSS**: Utility-first CSS framework
- **Radix UI**: Accessible component primitives
- **Framer Motion**: Smooth animations and transitions

### Backend
- **Next.js API Routes**: Serverless API endpoints
- **Prisma**: Type-safe database ORM
- **NextAuth.js**: Authentication and session management
- **bcryptjs**: Password hashing

### Database
- **PostgreSQL**: Robust relational database
- **Prisma Schema**: Well-structured data models

### UI Components
- **Custom Component Library**: Built with Radix UI primitives
- **Responsive Design**: Mobile-first approach
- **Dark/Light Mode**: Theme switching capability

## 📱 Responsive Design

ShopLinker is fully responsive and optimized for:
- **Desktop**: Full-featured experience with advanced layouts
- **Tablet**: Optimized touch interactions and layouts
- **Mobile**: Mobile-first design with touch-friendly interfaces

## 🔒 Security Features

- **Secure Authentication**: NextAuth.js with secure session management
- **Password Hashing**: bcryptjs for secure password storage
- **Role-Based Access Control**: Different permissions for customers, vendors, and admins
- **Input Validation**: Comprehensive validation using Zod schemas
- **CSRF Protection**: Built-in protection against cross-site request forgery

## 📈 Performance Optimizations

- **Image Optimization**: Next.js automatic image optimization
- **Code Splitting**: Automatic code splitting for faster loading
- **Static Generation**: Pre-rendered pages for better performance
- **Database Optimization**: Efficient queries with Prisma
- **Caching**: Strategic caching for improved response times

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ 
- PostgreSQL database
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd shoplinker/app
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Update the `.env` file with your database URL and authentication secrets:
   ```env
   DATABASE_URL="postgresql://username:password@localhost:5432/shoplinker"
   NEXTAUTH_URL="http://localhost:3000"
   NEXTAUTH_SECRET="your-secret-key"
   ```

4. **Set up the database**
   ```bash
   npx prisma generate
   npx prisma db push
   npx prisma db seed
   ```

5. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

6. **Open your browser**
   Navigate to `http://localhost:3000` to see the application.

## 📚 Documentation

- **[Deployment Guide](./docs/DEPLOYMENT.md)**: Complete deployment instructions for various platforms
- **[API Documentation](./docs/API.md)**: API endpoints and usage examples
- **[Database Schema](./docs/DATABASE.md)**: Detailed database structure and relationships

## 🚀 Deployment

ShopLinker can be deployed on multiple platforms. See our [Deployment Guide](./docs/DEPLOYMENT.md) for detailed instructions on:

- **Vercel**: One-click deployment with automatic CI/CD
- **Netlify**: JAMstack deployment with form handling
- **Railway**: Full-stack deployment with database hosting
- **Docker**: Containerized deployment for any platform

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](./CONTRIBUTING.md) for details on:
- Code of conduct
- Development workflow
- Pull request process
- Issue reporting

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## 🙏 Acknowledgments

- **Next.js Team**: For the amazing React framework
- **Vercel**: For hosting and deployment platform
- **Prisma**: For the excellent database toolkit
- **Tailwind CSS**: For the utility-first CSS framework
- **Radix UI**: For accessible component primitives

## 📞 Support

For support and questions:
- **Documentation**: Check our comprehensive docs
- **Issues**: Report bugs via GitHub Issues
- **Discussions**: Join our community discussions
- **Email**: Contact us at support@shoplinker.com

---

**Built with ❤️ using Next.js, TypeScript, and modern web technologies.**
