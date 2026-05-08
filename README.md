> **Early Stage & Experimental** - This project is in early development and should be considered experimental.

# Try mip in the browser

This project let's you try [mip](https://mip.sh), a package manager for MATLAB, in your browser without installing anything. The rendered page has a [numbl](https://numbl.org) REPL embedded in it, so you can run the example commands as you read.

## Live page

* **Rendered**: [Try mip in the browser](https://magland.github.io/try-mip-browser/)
* **Source**: [index.md](https://raw.githubusercontent.com/magland/try-mip-browser/refs/heads/main/index.md)

## Runs on numbl, not MATLAB

numbl is like MATLAB but runs in the browser. mip commands work the same way in numbl as they do in MATLAB. However, packages requiring os-specific binaries without browser support will not work, although they will install. Pure MATLAB packages work, and so do packages that include a `numbl_wasm` build.

## How it's built

The page is a Markdown file rendered by GitHub Pages. The REPL is a `<numbl-embed mode="repl">` element from [numbl-embed.js](https://numbl.org/numbl-embed.js).
