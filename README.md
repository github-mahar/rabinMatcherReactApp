# 🔍 Rabin Matcher: Client-Side Plagiarism Detection

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📌 Overview

**Rabin Matcher** is a high-performance, client-side plagiarism detection web application that demonstrates the **Rabin-Karp string matching algorithm**. Unlike traditional server-based checkers, all computation happens in the browser, enabling **instant analysis** without backend API calls.

It showcases how computationally intensive tasks can be efficiently handled on the client side for **educational and demonstrative purposes**.

---

## ✨ Key Features

- **Real-time Analysis**: Instantly detects similarities in the browser
- **Plagiarism Heatmap**: Color-coded visualization of exact and partial matches
- **Modern UI**: Responsive interface built with Tailwind CSS and React
- **Type Safety**: Fully typed TypeScript implementation for maintainable code

---

## ⚙️ Algorithmic Core

The core logic is in `src/lib/rabinKarp.ts` using a **rolling hash technique** for efficient string matching.

### Rolling Hash Example

```typescript
// Calculate initial hash for a pattern
function calculateHash(str: string, length: number): number {
  let hash = 0;
  for (let i = 0; i < length; i++) {
    hash = (hash * BASE + str.charCodeAt(i)) % PRIME;
  }
  return hash;
}

// Recalculate hash using rolling hash
function recalculateHash(
  oldHash: number,
  oldChar: string,
  newChar: string,
  patternLength: number,
  h: number
): number {
  let newHash = (oldHash - oldChar.charCodeAt(0) * h) % PRIME;
  newHash = (newHash * BASE + newChar.charCodeAt(0)) % PRIME;

  if (newHash < 0) newHash += PRIME;
  return newHash;
}
```

**Parameters:**

- `BASE = 256` → character set size
- `PRIME = 101` → prime for modulo
- `h = BASE^(patternLength-1) % PRIME` → precomputed multiplier

**Time complexity:** O(N + M), where N = text length, M = pattern length

---

## 📂 Project Structure

```
rabin-matcher/
├── bun.lockb
├── components.json
├── eslint.config.js
├── index.html
├── package.json
├── postcss.config.js
├── tailwind.config.ts
├── tsconfig.app.json
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
├── public/
│   └── robots.txt
└── src/
    ├── App.css
    ├── App.tsx
    ├── index.css
    ├── main.tsx
    ├── vite-env.d.ts
    ├── components/
    │   ├── AlgorithmInfo.tsx
    │   ├── NavLink.tsx
    │   ├── ResultsPanel.tsx
    │   ├── TextInput.tsx
    │   └── ui/
    │       ├── accordion.tsx
    │       ├── alert-dialog.tsx
    │       ├── alert.tsx
    │       ├── aspect-ratio.tsx
    │       ├── avatar.tsx
    │       ├── badge.tsx
    │       ├── breadcrumb.tsx
    │       ├── button.tsx
    │       ├── calendar.tsx
    │       ├── card.tsx
    │       ├── carousel.tsx
    │       ├── chart.tsx
    │       ├── checkbox.tsx
    │       ├── collapsible.tsx
    │       ├── command.tsx
    │       ├── context-menu.tsx
    │       ├── dialog.tsx
    │       ├── drawer.tsx
    │       ├── dropdown-menu.tsx
    │       ├── form.tsx
    │       ├── hover-card.tsx
    │       ├── input-otp.tsx
    │       ├── input.tsx
    │       ├── label.tsx
    │       ├── menubar.tsx
    │       ├── navigation-menu.tsx
    │       ├── pagination.tsx
    │       ├── popover.tsx
    │       ├── progress.tsx
    │       ├── radio-group.tsx
    │       ├── resizable.tsx
    │       ├── scroll-area.tsx
    │       ├── select.tsx
    │       ├── separator.tsx
    │       ├── sheet.tsx
    │       ├── sidebar.tsx
    │       ├── skeleton.tsx
    │       ├── slider.tsx
    │       ├── sonner.tsx
    │       ├── switch.tsx
    │       ├── table.tsx
    │       ├── tabs.tsx
    │       ├── textarea.tsx
    │       ├── toast.tsx
    │       ├── toaster.tsx
    │       ├── toggle-group.tsx
    │       ├── toggle.tsx
    │       ├── tooltip.tsx
    │       └── use-toast.ts
    ├── hooks/
    │   ├── use-mobile.tsx
    │   └── use-toast.ts
    ├── lib/
    │   ├── rabinKarp.ts
    │   └── utils.ts
    └── pages/
        ├── Index.tsx
        └── NotFound.tsx
```

---

## 🚀 Installation & Setup

### Prerequisites

- Node.js v16+ or Bun
- npm or Bun package manager

### Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/github-mahar/rabinMatcherReactApp.git
   cd rabin-matcher
   ```

2. **Install dependencies:**
   ```bash
   # Using npm
   npm install

   # Using bun
   bun install
   ```

3. **Start the development server:**
   ```bash
   # Using npm
   npm run dev

   # Using bun
   bun run dev
   ```

4. **Open your browser:** http://localhost:5173

### Build for Production

To build the project for production:

```bash
# Using npm
npm run build

# Using bun
bun run build
```

The built files will be in the `dist/` directory.

---

## 📖 Usage

1. Enter the original text in the first input field
2. Enter the suspected plagiarized text in the second field
3. Adjust the window size if needed (default: 5 words)
4. Click **Analyze** to run the detection
5. View the heatmap visualization and detailed analysis

---

## 🛠️ Technologies Used

- **React 18+** – modern functional components with hooks
- **TypeScript** – strong typing and maintainable code
- **Vite** – fast development and build tool
- **Tailwind CSS** – responsive utility-first styling
- **ESLint & Prettier** – code quality and formatting
- **PostCSS** – CSS processing

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repo
2. Create a branch (`git checkout -b feature-name`)
3. Commit your changes (`git commit -m "feat: description"`)
4. Push to the branch (`git push origin feature-name`)
5. Open a Pull Request

For major changes, please open an issue first.

---

## 📄 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

## 📚 Learn More

- [Rabin-Karp Algorithm](https://en.wikipedia.org/wiki/Rabin%E2%80%93Karp_algorithm)
- [Rolling Hash](https://cp-algorithms.com/string/string-hashing.html)
- [React Documentation](https://react.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)

---
