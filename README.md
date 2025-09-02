# 🚀 Next.js Learning Project - Dashboard Application

[![Next.js](https://img.shields.io/badge/Next.js-15.5.1-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.0.0-blue?style=for-the-badge&logo=react)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7.3-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.4.17-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-3.4.6-336791?style=for-the-badge&logo=postgresql)](https://www.postgresql.org/)
[![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com/)
[![Deployed](https://img.shields.io/badge/Status-Deployed-green?style=for-the-badge)](https://vercel.com/)

## 📚 Project Overview

This is a comprehensive **learning project** built with **Next.js 15** that demonstrates various advanced concepts and best practices. The project is a full-stack dashboard application for managing invoices and customers, implementing real-world patterns and optimizations.

**All templates were already styled and ready to use**

## 🎯 Learning Objectives Achieved

### 1. 🎨 **Font & Image Optimization**
- **Google Fonts Integration**: Implemented `Inter` and `Lusitana` fonts using `next/font/google`
- **Font Optimization**: Automatic font optimization with proper subsetting and preloading
- **Image Optimization**: Used `next/image` component for automatic image optimization
- **Responsive Images**: Implemented responsive hero images for desktop and mobile
- **Performance**: Reduced Cumulative Layout Shift (CLS) with proper image dimensions

### 2. 🔄 **Streaming & Suspense**
- **Static Streaming**: Implemented static streaming for dashboard components
- **Dynamic Streaming**: Used Suspense boundaries for loading states
- **Skeleton Loading**: Created skeleton components for better UX during data fetching
- **Progressive Loading**: Dashboard loads progressively with Suspense fallbacks

### 3. 📝 **Data Mutations & Server Actions**
- **Server Actions**: Implemented `"use server"` directives for form handling
- **Form Validation**: Used Zod schema validation for robust form handling
- **Database Operations**: CRUD operations for invoices with PostgreSQL
- **Revalidation**: Implemented `revalidatePath` for cache invalidation
- **Error Handling**: Comprehensive error handling with user-friendly messages

### 4. 🏗 **Modern Next.js Architecture**
- **App Router**: Utilized Next.js 15 App Router with route groups
- **Server Components**: Implemented React Server Components for better performance
- **Layout System**: Nested layouts with proper organization
- **Route Protection**: Authentication middleware and protected routes

### 5. 🎭 **Authentication & Security**
- **NextAuth.js**: Implemented authentication with NextAuth.js 5
- **Protected Routes**: Middleware-based route protection
- **Form Security**: Server-side validation and sanitization
- **Session Management**: Proper session handling and user context

## 🛠 Technology Stack

### **Frontend**
- **Next.js 15.5.1** - React framework with App Router
- **React 19** - Latest React with concurrent features
- **TypeScript 5.7.3** - Type-safe development
- **Tailwind CSS 3.4.17** - Utility-first CSS framework
- **Heroicons** - Beautiful SVG icons

### **Backend & Database**
- **PostgreSQL** - Relational database
- **Postgres.js** - Lightweight PostgreSQL client
- **NextAuth.js 5** - Authentication framework
- **Zod** - Schema validation library

### **Development Tools**
- **ESLint** - Code linting
- **Turbopack** - Fast bundler for development
- **pnpm** - Fast package manager

## 🚀 Features

### **Dashboard**
- 📊 Revenue charts with streaming data
- 💳 Real-time card statistics
- 📋 Latest invoices with pagination
- 👥 Customer management system

### **Invoice Management**
- ➕ Create new invoices
- ✏️ Edit existing invoices
- 🗑️ Delete invoices
- 📊 Status tracking (pending/paid)
- 🔍 Search and filter functionality

### **Customer Management**
- 👤 Customer profiles with avatars
- 📧 Contact information
- 💰 Invoice history
- 🖼️ Profile image management

### **Authentication**
- 🔐 Secure login system
- 🛡️ Protected routes
- 👤 User session management
- 🔒 Middleware-based security

## 📁 Project Structure

```
app/
├── dashboard/           # Dashboard routes
│   ├── (overview)/     # Route group for overview
│   ├── customers/      # Customer management
│   ├── invoices/       # Invoice management
│   └── layout.tsx      # Dashboard layout
├── ui/                 # Reusable UI components
│   ├── dashboard/      # Dashboard-specific components
│   ├── invoices/       # Invoice-related components
│   └── fonts.ts        # Font configurations
├── lib/                # Utility functions and data
│   ├── actions.ts      # Server actions
│   ├── data.ts         # Data fetching functions
│   └── utils.ts        # Helper utilities
└── layout.tsx          # Root layout
```

## 🚀 Getting Started

### **Prerequisites**
- Node.js 18+ 
- PostgreSQL database
- pnpm (recommended) or npm

### **Installation**

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd 21-nextjs-learning-project
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Environment Setup**
   Create a `.env.local` file:
   ```env
   POSTGRES_URL=your_postgres_connection_string
   AUTH_SECRET=your_auth_secret
   ```

4. **Database Setup**
   ```bash
   pnpm run seed
   ```

5. **Run Development Server**
   ```bash
   pnpm dev
   ```

6. **Build for Production**
   ```bash
   pnpm build
   pnpm start
   ```

## 🌐 Deployment

This project is deployed on **Vercel** and demonstrates production-ready optimizations:

- ✅ **Automatic Image Optimization**
- ✅ **Font Optimization & Preloading**
- ✅ **Static Generation with ISR**
- ✅ **Edge Runtime Support**
- ✅ **Performance Monitoring**

## 📖 Key Learning Concepts

### **Font Optimization**
```typescript
import { Inter, Lusitana } from 'next/font/google';

export const inter = Inter({ subsets: ['latin'] });
export const lusitana = Lusitana({ 
  weight: ['400', '700'], 
  subsets: ['latin'] 
});
```

### **Image Optimization**
```typescript
import Image from 'next/image';

<Image
  src="/hero-desktop.png"
  width={1000}
  height={760}
  alt="Dashboard screenshot"
  priority
/>
```

### **Server Actions**
```typescript
"use server";

export async function createInvoice(prevState: State, formData: FormData) {
  // Server-side logic with validation
  const validatedFields = CreateInvoice.safeParse({
    customerId: formData.get("customerId"),
    amount: formData.get("amount"),
    status: formData.get("status"),
  });
  
  // Database operation and revalidation
  revalidatePath("/dashboard/invoices");
  redirect("/dashboard/invoices");
}
```

### **Suspense & Streaming**
```typescript
<Suspense fallback={<CardsSkeleton />}>
  <CardWrapper />
</Suspense>
```

## 🔧 Development Commands

```bash
# Development
pnpm dev          # Start development server with Turbopack

# Building
pnpm build        # Build for production
pnpm start        # Start production server

# Code Quality
pnpm lint         # Run ESLint

# Database
pnpm run seed     # Seed database with sample data
```

## 📚 Resources & References

- [Next.js Learn Course](https://nextjs.org/learn/) - Official learning path
- [Next.js Documentation](https://nextjs.org/docs) - Comprehensive docs
- [React Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components)
- [App Router](https://nextjs.org/docs/app/building-your-application/routing)
- [Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)

## 🤝 Contributing

This is a learning project, but feel free to:
- 🐛 Report bugs
- 💡 Suggest improvements
- 📚 Share learning insights
- ⭐ Star the repository

## 📄 License

This project is created for educational purposes as part of the Next.js learning journey.

## 🙏 Acknowledgments

- **Vercel Team** - For the excellent Next.js framework and learning materials
- **Next.js Community** - For continuous improvements and documentation
- **Open Source Contributors** - For the amazing libraries and tools

---

**Built with ❤️ using Next.js 15** | **Deployed on Vercel** | **Learning in Progress** 🚀
