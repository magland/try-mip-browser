> **Early Stage & Experimental** - This project is in early development and should be considered experimental.

# Try mip in the browser

Try [mip](https://mip.sh), a package manager for MATLAB, in your browser without installing anything. The page has a [numbl](https://numbl.org) REPL embedded in it, so you can run the example commands as you read.

## Live page

* **Rendered**: [Try mip in the browser](https://magland.github.io/try-mip-browser/)
* **Source**: [index.md](https://raw.githubusercontent.com/magland/try-mip-browser/refs/heads/main/index.md)

## Runs on numbl, not MATLAB

numbl is like MATLAB but runs in the browser. mip commands work the same way here as they do in MATLAB. The catch is that a package shipping compiled MEX for Linux, Mac, or Windows but no browser build will install fine and then fail when you actually call its compiled functions. Pure MATLAB packages work, and so do packages that include a `numbl_wasm` build.

## How it's built

The page is a Markdown file rendered by GitHub Pages. The REPL is a `<numbl-embed mode="repl">` element from [numbl-embed.js](https://numbl.org/numbl-embed.js).
