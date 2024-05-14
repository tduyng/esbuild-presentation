---
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Esbuild
  An extremely fast bundler for the web

  Learn more at [Esbuild](https://esbuild.github.io)
drawings:
  persist: false
title: Esbuild presentation
transition: fade-out
mdc: true
hideInToc: true
fonts:
  sans: 'Robot' # basically the text
  serif: 'Robot Slab' # use with `font-serif` css class from windicss
  mono: 'Fira Code' # for code blocks, inline code, etc.
---
<div class='text-5xl'>
<img src='public/esbuild-logo.svg' class='m-0 slidev-icon-btn' />
Esbuild
</div>

**An extremely fast bundler for the web**

<div class='abs-br m-6 flex gap-2'>
<button @click='slidev.nav.openInEditor()' title='Open in Editor' class='text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white'>
  <carbon:edit />
</button>
<a href='https://github.com/evanw/esbuild' target='_blank' alt='GitHub' title='Open in GitHub'
  class='text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white'>
  <carbon-logo-github />
</a>
</div>

---
src: ./pages/about.md
hide: false
---

---
hideInToc: true
---
# Summary

<Toc />

---

# Display editor edit and Github repo

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>
---

# Hide toc
---
layout: default
hideInToc: true
---