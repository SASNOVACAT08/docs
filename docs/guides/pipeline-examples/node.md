---
title: Node Example
---

This is a simple example of a Node.js project using Katoa.

It has a single job that installs dependencies and runs the build script.

```typescript
import { Job, Pipeline } from "https://deno.land/x/katoa/mod.ts";

const build = new Job({
  name: "Node Build",
  image: "node",
  steps: [
    {
      name: "Install Dependencies",
      run: "npm install",
      cacheDirectories: ["node_modules"],
    },
    {
      name: "Run build",
      run: "npm run build",
      cacheDirectories: ["node_modules"],
    },
  ],
});

export default new Pipeline([build]);
```