It seems that Hono('s `@hono/vite-dev-server`) breaks Vite's HMR.

Reproduction:

```
pnpm install
pnpm run dev
```

Then:
- Go to http://localhost:3000
- Click on the counter button
- Make some change
  ```diff
  // pages/index/+Page.tsx

  - <h1>My Vike app</h1>
  + <h1>My Vike apppppp</h1>
  ```
- Observe how the counter is reset to `0`. This means the page was fully reloaded and HMR doesn't work.

HMR works when using the exact same application using Express.js instead of Hono.
