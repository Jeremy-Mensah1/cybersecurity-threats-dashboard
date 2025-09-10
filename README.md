# Jeremy Mensah — Portfolio repository (ready-to-use)

This document contains a complete, ready-to-copy GitHub repository structure and all files you'll need to publish a single-page React portfolio (Tailwind CSS) focused on **Data Analysis**, **Disaster Management**, and an optional **Gospel Corner**. Theme color: **red**. Personal details and projects are prefilled using the information I have.

> **Your GitHub username:** `Jeremy-Mensa1`
> **Email:** `mensahjeremy353@gmail.com`
> **Phone:** `+233539251740`

---

## Repo layout (one-line summary of each file)

```
portfolio-jeremy/                # root folder
├─ README.md
├─ package.json
├─ tailwind.config.js
├─ postcss.config.js
├─ public/
│  └─ index.html
├─ src/
│  ├─ main.jsx
│  ├─ App.jsx
│  ├─ index.css
│  └─ components/
│     ├─ Header.jsx
│     ├─ About.jsx
│     ├─ Projects.jsx
│     ├─ Contact.jsx
│     └─ Footer.jsx
├─ assets/
│  ├─ images/
│  │  ├─ cybersecurity-dashboard.jpg   # add your JPG here
│  │  ├─ stock-dashboard.jpg
│  │  └─ hr-analytics-dashboard.jpg
└─ .github/
   └─ workflows/
      └─ github-pages.yml
```

---

## README.md (copy to repo root)

```markdown
# Jeremy Mensah — Data Analysis & Disaster Management Portfolio

This is a single-page React + Tailwind portfolio showcasing Power BI and data analysis projects, plus information about disaster management and a small Gospel Corner.

## Live demo
Deploy this repository to GitHub Pages (instructions below) or Vercel/Netlify.

## Projects included
- Cybersecurity Dashboard (Power BI screenshot)
- Stock Performance Dashboard (Power BI)
- Human Resource Analytics Dashboard (Power BI)

## Personal Info
- **Name:** Jeremy Mensah
- **Email:** mensahjeremy353@gmail.com
- **Phone:** +233539251740
- **GitHub:** @Jeremy-Mensa1

## How to run locally
1. `git clone https://github.com/Jeremy-Mensa1/portfolio-jeremy.git`
2. `cd portfolio-jeremy`
3. `npm install`
4. `npm run dev` (or `npm run build && npm run deploy` to publish)

## Deployment (GitHub Pages)
This repo includes a GitHub Actions workflow to publish to `gh-pages` branch automatically when you push to `main`.

## License
MIT
```

---

## `package.json` (minimal)

```json
{
  "name": "portfolio-jeremy",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "vite": "^5.0.0",
    "tailwindcss": "^4.0.0",
    "postcss": "^8.0.0",
    "autoprefixer": "^10.0.0",
    "gh-pages": "^5.0.0"
  }
}
```

---

## `tailwind.config.js`

```js
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,jsx}'],
  theme: {
    extend: {
      colors: {
        brand: {
          DEFAULT: '#b91c1c', // reddish brand color
          light: '#ef4444'
        }
      }
    }
  },
  plugins: []
}
```

---

## `public/index.html`

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Jeremy Mensah — Portfolio</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

---

## `src/main.jsx`

```jsx
import React from 'react'
import { createRoot } from 'react-dom/client'
import App from './App'
import './index.css'

createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)
```

---

## `src/index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

html, body, #root { height: 100%; }
body { @apply bg-white text-gray-800; }
```

---

## `src/App.jsx` (single-file app that imports components)

```jsx
import React from 'react'
import Header from './components/Header'
import About from './components/About'
import Projects from './components/Projects'
import Contact from './components/Contact'
import Footer from './components/Footer'

export default function App() {
  return (
    <div className="min-h-screen flex flex-col">
      <Header />
      <main className="flex-grow container mx-auto px-4 py-8">
        <About />
        <Projects />
        <Contact />
      </main>
      <Footer />
    </div>
  )
}
```

---

## Components (copy each file into `src/components/`)

### `Header.jsx`

```jsx
export default function Header(){
  return (
    <header className="bg-brand text-white py-6">
      <div className="container mx-auto px-4 flex items-center justify-between">
        <h1 className="text-2xl font-bold">Jeremy Mensah</h1>
        <nav>
          <a href="#about" className="mr-4">About</a>
          <a href="#projects" className="mr-4">Projects</a>
          <a href="#contact">Contact</a>
        </nav>
      </div>
    </header>
  )
}
```

### `About.jsx`

```jsx
export default function About(){
  return (
    <section id="about" className="py-10">
      <h2 className="text-xl font-semibold mb-4">About me</h2>
      <p className="max-w-2xl">I am Jeremy Mensah — data analyst and disaster management diploma holder. I build practical Power BI dashboards and help organisations visualise threats and performance. I studied data analytics at BIZMARROW Technologies and I am currently studying BSc Business Computing & Information Systems at IPMC. I am passionate about helping organisations become data-driven while keeping God at the centre of my decisions.</p>
      <ul className="mt-4">
        <li>- Diploma in Disaster Management</li>
        <li>- Data Analysis: Excel, Power BI, SQL</li>
        <li>- Teaching experience and report compilation</li>
      </ul>
    </section>
  )
}
```

### `Projects.jsx`

```jsx
export default function Projects(){
  const projects = [
    {title: 'Cybersecurity Dashboard (Power BI)', img: '/assets/images/cybersecurity-dashboard.jpg', desc: 'Incident visualisation and loss analysis (2020-2024).'},
    {title: 'Stock Performance Dashboard', img: '/assets/images/stock-dashboard.jpg', desc: 'Adj Close, Volume and trend analysis.'},
    {title: 'HR Analytics Dashboard', img: '/assets/images/hr-analytics-dashboard.jpg', desc: 'Staff satisfaction, churn & promotion analysis.'}
  ]

  return (
    <section id="projects" className="py-10">
      <h2 className="text-xl font-semibold mb-6">Selected projects</h2>
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {projects.map((p) => (
          <article key={p.title} className="border rounded-lg overflow-hidden shadow-sm">
            <img src={p.img} alt={p.title} className="w-full h-48 object-cover" />
            <div className="p-4">
              <h3 className="font-semibold">{p.title}</h3>
              <p className="text-sm mt-2">{p.desc}</p>
            </div>
          </article>
        ))}
      </div>
    </section>
  )
}
```

### `Contact.jsx`

```jsx
export default function Contact(){
  return (
    <section id="contact" className="py-10">
      <h2 className="text-xl font-semibold mb-4">Contact</h2>
      <p>Email: mensahjeremy353@gmail.com</p>
      <p>Phone: +233539251740</p>
      <p className="mt-4">Want my CV or to discuss a Power BI project? Send an email or connect on GitHub: <a href="https://github.com/Jeremy-Mensa1">@Jeremy-Mensa1</a></p>
    </section>
  )
}
```

### `Footer.jsx`

```jsx
export default function Footer(){
  return (
    <footer className="bg-gray-100 py-4">
      <div className="container mx-auto px-4 text-center text-sm">© {new Date().getFullYear()} Jeremy Mensah — Built with React & Tailwind</div>
    </footer>
  )
}
```

---

## `.github/workflows/github-pages.yml` (deploy on push to main)

```yaml
name: Deploy React App to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm run build
      - run: npm run deploy
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

> NOTE: The `gh-pages` script in package.json will publish the `dist` folder. Alternatively, you can use `peaceiris/actions-gh-pages` for a more robust deployment.

---

## What you should add/upload from your laptop

* `assets/images/cybersecurity-dashboard.jpg` (from your Data Portfolio → Power BI Project folder)
* `assets/images/...` other screenshots
* Your CV (PDF) into `/public/docs/CV-Jeremy-Mensah.pdf` and link to it from Contact if you want

---

## Quick Git commands (one-shot)

```bash
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/Jeremy-Mensa1/portfolio-jeremy.git
git push -u origin main
```

---

## Final notes & tips

* The repository is prefilled with your personal contact and project names. If any of that changed, open `src/components/About.jsx` and `Contact.jsx` and update.
* If you prefer a plain HTML/CSS site (no React), tell me and I will generate it instead.
* To make the site more discoverable, add a short `meta description` in `public/index.html` and pin the repo on GitHub.

---

If you'd like, I can now:

* produce a ready-to-paste ZIP with all these files (I can generate the files here in the canvas), or
* generate a plain HTML version instead of React, or
* create a tailored GitHub Actions workflow for Netlify/Vercel.

Tell me which of the three you'd like and I'll prepare it immediately.
