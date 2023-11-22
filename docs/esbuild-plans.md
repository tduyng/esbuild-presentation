# Esbuild
An extremely fast bundler for the web

# Action plan
- What is esbuild?
- Major features
- Who use esbuild?
- Why is it fast?
- A quick start


# What is esbuild?

It is an extremely fast JavaScript and CSS bundler and minifier. 

Current build tools for the web are 10-100x slower than they could be. 

The main goal of this project is to bring about a new era of build tool performance, and create an easy-to-use modern bundler along the way

- It developed by Evan Wallace, creator of Figma
- Written in Go
- First release: 2020
- 36.5k stars sur github

## Performance

- [Twitter](https://twitter.com/evanwallace/status/1448714353386086405)
- [Learn more about benchmark details](https://esbuild.github.io/faq/#benchmark-details)


# Major features

- Extreme speed without needing a cache
- JavaScript, CSS, TypeScript, and JSX built-in
- An API for CLI, JS, and Go
- Plugins
- Bundles ESM and CommonJS modules
- Bundles CSS including CSS modules
- Tree shaking, minification, and source maps
- Local server, watch mode, and plugins

# Who use esbuild?

```mermaid
mindmap
  root((esbuild))
    Who use esbuild
      Angular
      Typescript repo
      Vite
      Snowpack
      Amazon CDK
      Phoenix framework
      Remix run
      SvelteKit
      Yarn's Plug'n'Play
      Tsx
      Esbuild-register
    Compiled languages
      Js
      Ts
      Jsx
      Tsx
      Css
```

# Why is it fast?

- It's written in Go and compiles to native code
- Parallelism is used heavily
- Everything in esbuild is written from scratch
- Memory is used efficiently

Each one of these factors is only a somewhat significant speedup,
but together they can result in a bundler that is multiple orders of magnitude faster than other bundlers commonly in use today


# A quick start

## CLI mode

```md
# Install
npm add -D esbuild

# Add build command to package.json
"scripts": {
    "build-dev": "esbuild src/index.ts --bundle --platform=node --outfile=dist/index.js --format=esm --target=es2022",
    "build": "tsc --noEmit && build-dev",
    "watch": "esbuild src/index.ts --bundle --watch --platform=node --outfile=dist/index.js --format=esm --target=es2022"
}

--bundle indicates that it should output only one file containing our entire bundle.
--platform=node indicates that it should bundle for Node.js.
--outfile=dist/index.js indicates that it should output the bundle to dist/index.js.
--format=esm indicates that it should use ES Modules for imports and exports.
```

[Learn more about the build options](https://esbuild.github.io/api/#build)

## Scripts mode

```md
# build.js
import esbuild from'esbuild'
import fp from 'fast-glob'

const entryPoints = fg.sync(['src/**/*.[tj]s'])

esbuild
    .build({
            entryPoints,
            outdir: 'dist',
            platform: 'node',
            sourcemap: true,
            target: 'es2022',
            format: 'esm',
    })
    .catch(() => process.exit(1))

```
## An Extremely Simple React Starter Kit
```md
# Project structure
src/
├─ components/
│  ├─ app.module.css
│  ╰─ app.tsx
├─ index.html
├─ index.tsx
├─ livereload.js
├─ style.css
╰─ types.d.ts

# livereload.js
new EventSource("/esbuild").addEventListener("change", () => location.reload());

# dev server command
esbuild src/index.html src/index.tsx \
  --loader:.html=copy \
  --outdir=build --bundle --watch \
  --servedir=build --serve-fallback=src/index.html \
  --inject:src/livereload.js
```

[See more](https://jakelazaroff.com/words/an-extremely-simple-react-starter-kit/)
