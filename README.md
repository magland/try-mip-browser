> **Early Stage & Experimental** - This project is in early development and should be considered experimental.

# Try mip in the browser

A self-contained tutorial that lets you try [mip](https://mip.sh), a package manager for MATLAB, directly in the browser with no installation. The page embeds an interactive [numbl](https://numbl.org) REPL via [numbl-embed](https://github.com/flatironinstitute/numbl) so you can run the example commands inline.

## Live page

* **Rendered**: [Try mip in the browser](https://magland.github.io/try-mip-browser/)
* **Source**: [index.md](https://raw.githubusercontent.com/magland/try-mip-browser/refs/heads/main/index.md)

## Powered by numbl, not MATLAB

The REPL runs [numbl](https://numbl.org), a MATLAB-compatible numerical computing environment that runs in the browser. mip itself works the same as it does in MATLAB: listing channels, resolving dependencies, inspecting, installing, loading, unloading, uninstalling. The catch is at runtime. Packages that depend on OS-specific MEX binaries with no `numbl_wasm` build will install fine but their compiled functions won't execute in the browser. Pure-MATLAB packages (`any`) and packages with a `numbl_wasm` build run normally.

## How it's built

The page is plain Markdown rendered by GitHub Pages. The interactive REPL comes from a `<numbl-embed mode="repl">` element backed by [numbl-embed.js](https://numbl.org/numbl-embed.js).
