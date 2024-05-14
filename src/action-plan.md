# Esbuild
An extremely fast bundler for the web

# Action plan
- What is esbuild?
- Major features
- Benchmark
- Who use esbuild?
- Ecosystem
- Why is it fast?
- A quick start


# What is esbuild?

It is an extremely fast JavaScript and CSS bundler and minifier. Current build tools for the web are 10-100x slower than they could be.The main goal of this project is to bring about a new era of build tool performance, and create an easy-to-use modern bundler along the way

- Developed by Evan Wallace, creator of Figma
- Written in Go
- First release: 2020
- 37.4k stars sur Github

# Major features

- Extreme speed without needing a cache
- JavaScript, CSS, TypeScript, and JSX built-in
- A straightforward API for CLI, JS, and Go
- Bundles ESM and CommonJS modules
- Bundles CSS including CSS modules
- Tree shaking, minification, and source maps
- Local server, watch mode, and plugins

# Benchmark

- [Twitter 1448714353386086405](https://twitter.com/evanwallace/status/1448714353386086405)
- [Twitter 1459587741843394569](https://twitter.com/evanwallace/status/1459587741843394569)

Performance benchmark for most popular javascript bundlers in various configurations

|                         | **Empty** | **Libraries** | **Mui** | Synthetic     |
|-------------------------|-----------|---------------|---------|---------------|
| Esbuild                 | 0.046     | 0.142         | 0.192   | 0.685         |
| Parcel: babel + terser  | 3.737     | 11.529        | 8.892   | 57.232        |
| Rollup: babel + terser  | 3.121     | 13.056        | 9.495   | 37.689        |
| Rollup: esbuild         | 1.874     | 5.553         | 5.746   | 14.612        |
| Rollup: swc             | 1.788     | 5.966         | 5.802   | 14.644        |
| Rspack                  | 0.192     | 1.308         | 0.607   | 5.730         |
| Vite                    | 1.418     | 6.632         | 7.957   | 36.735        |
| Webpack: babel + terser | 2.471     | 11.529        | 6.406   | 23.889        |
| Webpack: esbuild        | 0.808     | 3.145         | 2.665   | 8.798         |
| Webpack: swc            | 0.849     | 4.033         | 2.927   | 9.134         |

<img src="public/build-time.png" alt="Build time" loading="lazy">

# Who use esbuild?

```mermaid { theme: 'forest'}
mindmap
  root((esbuild))
    Frameworks
      Angular
      React
      Vue
      Astro
      Solid
      Phoenix
      Remix
      Svelte
      Lit
      Nuxt
      Node
      Bun
      Amazon CDK
    Tools
      Vite
      Snowpack
      Stackblitz
      Typescript
      Yarn
      Tsx
      Esbuild-register
      Zx
    Languages
      Javascript
      JSX
      Typescript
      TSX
      CSS
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

```py
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

```py
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

```py
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
