# SSA Solutions - Facilities Management

A modern, responsive web application for SSA Solutions, a professional facilities management and cleaning services company based in Bangalore, India.

## Tech Stack

- **React 18** with TypeScript
- **Vite** for fast development and builds
- **Tailwind CSS** for styling
- **shadcn/ui** component library
- **Framer Motion** for animations
- **React Hook Form** + Zod for form validation
- **Wouter** for client-side routing
- **EmailJS** for contact form submissions

## Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for Production

```bash
npm run build
```

The output will be in the `dist/` folder.

### Preview Production Build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/
│   └── ui/          # Reusable UI components (shadcn/ui)
├── hooks/           # Custom React hooks
├── lib/             # Utility functions
├── pages/           # Page components
├── App.tsx          # Root component & routing
├── main.tsx         # Entry point
└── index.css        # Global styles
```

## Deployment

This app can be deployed to Netlify, Vercel, or any static hosting provider.

### Netlify
1. Run `npm run build`
2. Upload the `dist/` folder to Netlify

### Vercel
Connect your GitHub repo to Vercel and it will auto-deploy on every push.
