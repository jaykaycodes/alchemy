# Assets

The Assets resource lets you add [static assets](https://developers.cloudflare.com/workers/configuration/sites/) to your Cloudflare Workers.

# Minimal Example

Create a basic assets bundle from a local directory:

```ts
import { Assets } from "alchemy/cloudflare";

const staticAssets = await Assets("static", {
  path: "./src/assets"
});
```

# Bind to a Worker

Use the assets with a worker:

```ts
import { Worker, Assets } from "alchemy/cloudflare";

const staticAssets = await Assets("static", {
  path: "./src/assets"
});

const worker = await Worker("frontend", {
  name: "frontend-worker", 
  entrypoint: "./src/worker.ts",
  bindings: {
    ASSETS: staticAssets
  }
});
```