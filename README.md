# vite-getting-started
Just a sanbox to try out vite

resources used are linked bellow:

[freeCodeCamp tutorial with React and TS](https://www.freecodecamp.org/news/how-to-migrate-from-create-react-app-to-vite/)
[StackBlitz Vite sandbox](https://vite.dev/guide/#trying-vite-online)

## Install vite and plugins for react and ts

```bash
npm install vite @vitejs/plugin-react vite-tsconfig-paths
```

optional: vite-plugin-svgr transforms svg into React components --- meh... cant find a strong reason to use it for now

## Vite [config](https://vite.dev/config/) file

vite.config.(js,ts) should contain the configs
One can use the helper function defineConfig to make sure intellisense (typing info) or custom code runs before returning the config object

```ts
import { defineConfig } from 'vite'

export default defineConfig({
  // ...
})
```
```ts
export default defineConfig(({ command, mode, isSsrBuild, isPreview }) => {
  if (command === 'serve') {
    return {
      // dev specific config
    }
  } else {
    // command === 'build'
    return {
      // build specific config
    }
  }
})
```
```ts
import { defineConfig, loadEnv } from 'vite'

export default defineConfig(({ command, mode }) => {
  // Load env file based on `mode` in the current working directory.
  // Set the third parameter to '' to load all env regardless of the `VITE_` prefix.
  const env = loadEnv(mode, process.cwd(), '')
  return {
    // vite config
    define: {
      __APP_ENV__: JSON.stringify(env.APP_ENV),
    },
  }
})
```

### Vite Types file
this is for intellisense only. Vite will provide type definitions in vite/client.d.ts
