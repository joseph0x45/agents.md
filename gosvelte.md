# GoSvelte Frontend Reference

## Stack
- **Svelte 5** with Vite, built as iife bundles
- **Tailwind CSS** via CDN
- One bundle per page — `home.js`, `dashboard.js`, etc.

## Structure
```
frontend/src/
├── entries/        ← one entry file per page
├── pages/          ← page-level components
└── components/     ← shared components
```

## Svelte 5
This project uses Svelte 5. Always use the new API:

```svelte
<script>
  let { username = 'Guest' } = $props()  // not "export let"
</script>

<svelte:head>
  <title>Home — {username}</title>
</svelte:head>

<div>
  <h1>Hello, {username}!</h1>
</div>
```

## Props
Props come from Go via `window.__INITIAL_DATA__` and are passed directly to the component on mount. Whatever keys the Go backend sends, those are the props available in the page component.

## HTML Template
The page component mounts on `<main id="app">`. Tailwind classes are available everywhere.

```html
<body class="bg-zinc-950 text-zinc-100">
  <main id="app"></main>
  <script>
    window.__INITIAL_DATA__ = {...};  <!-- injected by Go -->
  </script>
  <script src="/static/home.js"></script>
</body>
```
