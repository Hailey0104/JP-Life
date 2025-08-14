# JP-Life
https://github.com/Hailey0104/j-life-website
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/j-life-website.git
git push -u origin main
{
  "name": "j-life-website",
  "version": "1.0.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "framer-motion": "^11.0.0",
    "lucide-react": "^0.468.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.66",
    "@types/react-dom": "^18.2.22",
    "autoprefixer": "^10.4.18",
    "postcss": "^8.4.38",
    "tailwindcss": "^3.4.10",
    "vite": "^5.4.2"
  }
}

# J‑Life Website (React + Vite + Tailwind)

A production-ready static site for **J‑Life** — deploy in minutes to Vercel, Netlify, or any static host.

## Quick start (local)
```bash
# 1) Install dependencies
npm i

# 2) Run locally
npm run dev
# open the URL printed in your terminal
```

## Build
```bash
npm run build
# outputs to dist/
```

## Deploy to Vercel (recommended)
1. Create a free account at https://vercel.com and install Vercel CLI (optional).
2. Push this folder to a GitHub repo.
3. In Vercel: **New Project** → Import your repo → Framework **Vite** (auto-detected) → Deploy.
4. In Project → **Settings → Domains**, add your custom domain (e.g., jlifejapan.com). Follow DNS prompts.

## Deploy to Netlify
1. Create a free account at https://netlify.com.
2. **Add new site** → Import from Git → Build command: `npm run build` → Publish directory: `dist`.
3. Add your custom domain in **Domain settings** and update DNS as instructed.

## Connect the form
This demo form doesn’t send data. To receive submissions:
- **Formspree**: add the action URL to the `<form>` tag.
- **Netlify Forms**: add `data-netlify="true"` and deploy on Netlify.
- **Custom API**: replace the `submit()` in `App.jsx` with a `fetch()` POST.

## Customize
- Edit content in `src/App.jsx` (text, images, pricing).
- Tailwind styles are in `src/index.css` and utility classes inline.
- Replace contact details in the Apply section and Footer.

## License
Free for personal and commercial use.
