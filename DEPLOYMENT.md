# Deployment Guide

## Making This Available After Closing Blackbox Agent

This Next.js application is ready for deployment. Here are the steps to make it available after closing the Blackbox agent:

### Option 1: Netlify Deployment (Recommended)

1. **Push to GitHub**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/your-repo-name.git
   git push -u origin main
   ```

2. **Connect to Netlify**
   - Go to [Netlify](https://netlify.com)
   - Import from GitHub
   - Select your repository
   - Build command: `npm run build`
   - Publish directory: `.next`

3. **Environment Variables**
   Add these in Netlify dashboard:
   - `DATABASE_URL`
   - `NEXTAUTH_URL`
   - `NEXTAUTH_SECRET`
   - Any API keys needed

### Option 2: Vercel Deployment (Alternative)

1. **Install Vercel CLI**
   ```bash
   npm i -g vercel
   ```

2. **Deploy**
   ```bash
   vercel --prod
   ```

### Option 3: Local Development Server

1. **Build and Start**
   ```bash
   npm run build
   npm start
   ```

2. **Access at**: http://localhost:8000

### Option 4: Static Export (Fallback)

1. **Update next.config.ts**
   ```typescript
   const nextConfig: NextConfig = {
     output: 'export',
     images: {
       unoptimized: true
     }
   }
   ```

2. **Build**
   ```bash
   npm run build
   ```

3. **Deploy `out` folder to any static hosting**

## Quick Start Commands

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Start production server
npm start
```

## Environment Setup

1. Copy `.env.example` to `.env.local`
2. Fill in your actual values
3. Never commit `.env.local` to git

## Troubleshooting

- **Build fails**: Check Node.js version (should be 20+)
- **Database issues**: Ensure DATABASE_URL is set
- **Auth issues**: Check NEXTAUTH_SECRET and NEXTAUTH_URL
