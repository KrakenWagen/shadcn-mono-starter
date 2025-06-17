# shadcn/ui Monorepo Starter

A modern monorepo starter powered by [shadcn/ui](https://ui.shadcn.com/), [Next.js](https://nextjs.org/), [Tailwind CSS](https://tailwindcss.com/), and [Turborepo](https://turbo.build/).  

 🎉 This starter includes [Cursor](https://www.cursor.so/) workspace rules for best practices, structure, and development workflow. See the `.cursor/rules` directory for details.

Everything is preconfigured—just clone and start building!


---

## Table of Contents

1. [Monorepo Structure](#monorepo-structure)
2. [Development](#development)
3. [UI Components](#ui-components)
4. [Styling](#styling)
5. [Deployment](#deployment)
6. [Best Practices](#best-practices)
7. [Resources](#resources)

---

## Monorepo Structure

```
apps/
  web/                # Main Next.js app (App Router)
packages/
  ui/                 # Shared UI library (shadcn/ui + Tailwind)
  eslint-config/      # Shared ESLint config
  typescript-config/  # Shared TypeScript config
```

- **apps/web**: Your main web application.
- **packages/ui**: Reusable UI components, hooks, and styles.
- **packages/eslint-config**: Centralized ESLint rules.
- **packages/typescript-config**: Centralized TypeScript settings.

---

## Development

1. **Install dependencies** (from the repo root):

   ```bash
   pnpm install
   ```

2. **Start the development server**:

   ```bash
   pnpm run dev
   ```

   This runs the Next.js app in `apps/web`.

3. **Build all packages and apps**:

   ```bash
   pnpm run build

   #
   ```

4. **Lint and type-check**:

   ```bash
   pnpm run lint
   pnpm run check-types
   ```

---

## UI Components

- All shared UI lives in `packages/ui`.
- To add a new component (e.g., `button`):

  ```bash
  pnpm dlx shadcn@latest add button -c apps/web
  ```

  This will place the component in `packages/ui/src/components`.

- **Importing in your app:**

  ```tsx
  import { Button } from "@workspace/ui/components/button";
  ```

  > Replace `@workspace` with your actual monorepo scope if different.

- **Tailwind CSS** is preconfigured and ready to use.

---

## Styling

- Use Tailwind CSS utility classes for styling.
- Shared styles and utilities are in `packages/ui/src/styles` and `packages/ui/src/lib`.
- Use the `cn` utility for conditional class names:

  ```tsx
  import { cn } from "@workspace/ui/lib/utils";
  ```

---

## Deployment

You have two main options for deploying your app:

### A. Deploy to Vercel (Recommended)

- Use the included deploy script to deploy with Vercel:

  ```bash
  pnpm run deploy
  ```
  This runs the deploy script in `package.json`, which uses the Vercel CLI (`pnpx vercel`).

- The main app (`apps/web`) is a standard Next.js app and works seamlessly with Vercel.
- **Static HTML Output:** The Next.js app is configured to output static HTML using `output: "export"` in `next.config.mjs`. The build output is a static site in `apps/web/out`.
- For Vercel:
  - Set the root directory to `apps/web`.
  - Ensure `pnpm install` is used for installing dependencies.

### B. Manual Deployment (Any Platform)

- **Build for production:**

  ```bash
  pnpm run build
  ```

- **Start the production server:**

  ```bash
  pnpm run start
  ```

- **Static HTML Output:** The build output is a static HTML site in `apps/web/out` (configured via `output: "export"` in `next.config.mjs`).
- You can deploy the output to any platform that serves static sites or supports Next.js (e.g., Netlify, AWS, DigitalOcean, etc.).

---

## Best Practices

- Use `packages/ui` for all shared UI.
- Keep components modular, typed, and accessible.
- Prefer React Server Components and Suspense for performance.
- Use context for global state, keep state close to where it's used.
- Test complex components with React Testing Library.
- Follow accessibility guidelines (keyboard, ARIA, color contrast).

---

## Resources

- [shadcn/ui Documentation](https://ui.shadcn.com/docs)
- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Turborepo Documentation](https://turbo.build/repo/docs)
- [pnpm Documentation](https://pnpm.io/)
- [Cursor](https://www.cursor.com/en)

---

Feel free to customize this template to fit your project's needs!
