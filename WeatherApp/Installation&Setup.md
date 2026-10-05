# Weather App

A weather application built using **React + Vite**, styled with **Tailwind CSS**, with **Lucide React** used for icons.

## Tech Stack

* **React** — Frontend library
* **Vite** — Development server and build tool
* **JavaScript** — Programming language
* **Tailwind CSS** — Utility-first CSS framework
* **Lucide React** — Icon library
* **ESLint** — Code quality and linting

---

# 1. Project Setup

The project was created using Vite:

```bash
npm create vite@latest
```

### Configuration

The following options were selected:

```text
Project name: .
Package name: weatherapp
Framework: React
Variant: JavaScript
Linter: ESLint
Install dependencies: Yes
```

The project was created in:

```text
C:\Users\crimson\OneDrive\Desktop\REACT
```

---

# 2. Install Dependencies

After creating the project, the required dependencies were installed.

### Install Project Dependencies

```bash
npm install
```

### Install Tailwind CSS

Tailwind CSS and its Vite plugin were installed using:

```bash
npm install tailwindcss @tailwindcss/vite
```

---

# 3. Configure Tailwind CSS

## Configure the Vite Plugin

The Tailwind CSS Vite plugin was added to `vite.config.js`.

```javascript
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [react(),tailwindcss()],
})

```

## Import Tailwind CSS

Add an @import to your CSS file that imports Tailwind CSS.

```index.css
@import "tailwindcss";
```

Start using Tailwind in your HTML

```index.html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <link href="/src/index.css" rel="stylesheet">
    <title>Weather App</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>

```

This allows Tailwind utility classes to be used throughout the React application.

---

# 4. Lucide React Setup

Lucide React provides icons that can be used directly as React components.

Installation:

```bash
pnpm install lucide-react
```
### Package Manager

`pnpm` was not available in the environment, so npm was used instead.

```bash
npm install lucide-react
```


The icons can then be used inside React components:

---

# 5. Run the Development Server

The application can be started using:

```bash
npm run dev
```

Vite starts the development server at:

```text
http://localhost:5173/
```

The application can then be opened in a browser using the local URL.

---

# 6. Current Setup Status

### Completed

* [x] React project created using Vite
* [x] JavaScript configured
* [x] ESLint configured
* [x] Project dependencies installed
* [x] Tailwind CSS installed
* [x] Tailwind CSS Vite plugin configured
* [x] Tailwind CSS imported
* [x] Lucide React installed
* [x] Vite development server tested successfully

### Upcoming

* [ ] Build the weather application UI
* [ ] Create weather search functionality
* [ ] Integrate a weather API
* [ ] Display current weather information
* [ ] Add weather icons
* [ ] Add loading states
* [ ] Add error handling
* [ ] Add location-based weather
* [ ] Improve responsive design
* [ ] Test the completed application

---


* Error and loading handling
* Frontend project structure
