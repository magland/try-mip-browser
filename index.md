<script src="https://numbl.org/numbl-embed.js"></script>

# Try mip in the browser

[mip](https://mip.sh) is a package manager for MATLAB. This page lets you try it directly in your browser, no installation needed.

> **Powered by [numbl](https://numbl.org), not MATLAB.**
> numbl is a MATLAB-compatible numerical computing environment that runs in the browser via WebAssembly. mip itself works the same as it does in MATLAB: channels, resolution, install/load/list/uninstall all behave normally. The catch is at runtime. Packages that depend on OS-specific MEX binaries with no `numbl_wasm` build will install fine but their compiled functions won't execute in the browser. Pure-MATLAB packages (`any`) and packages with a `numbl_wasm` build run normally.

## Interactive REPL

Type the commands from the rest of this page into the REPL below. State (installed packages, loaded paths, workspace variables) persists for the life of the tab and is cleared on refresh.

<numbl-embed mode="repl">
<iframe width="100%" height="600" frameborder="0"></iframe>
</numbl-embed>

## A quick tour

### See the help

```
help mip
```

For details on any command:

```
mip help install
mip help avail
```

### List available packages

The default channel is `mip-org/core`:

```
mip avail
```

Try another channel, Flatiron Institute's, which hosts packages like `chunkie`, `finufft`, `fmm2d`, `flam`, and `surfacefun`:

```
mip avail --channel flatironinstitute
```

The list is filtered to packages compatible with the current architecture. In the browser that's `numbl_wasm`, with a fallback to `any` for pure-MATLAB packages.

### Install a package

`chebfun` is a numerical computing library for representing and computing with functions. It's pure MATLAB, so it installs cleanly in numbl:

```
mip install chebfun
```

mip resolves dependencies, downloads the package, and unpacks it into the in-browser virtual filesystem.

### Load it onto the path

```
mip load chebfun
```

Now chebfun is on the path and ready to use:

```matlab
f = chebfun(@(x) sin(10*x) .* exp(-x.^2), [-3, 3]);
plot(f)
title('A chebfun')
```

### See what's installed

```
mip list
```

### Inspect a package

```
mip info chebfun
```

You can also peek at packages you haven't installed:

```
mip info --channel flatironinstitute chunkie
```

### Unload and uninstall

```
mip unload chebfun
mip uninstall chebfun
```

`mip uninstall` also prunes any dependencies that were pulled in automatically and are no longer needed.

## Other things to try

- **A package with a browser MEX build.** `fmm2d` (Flatiron Institute's 2-D fast multipole methods) ships a `numbl_wasm` variant, so it installs and runs in the browser:
  ```
  mip install --channel flatironinstitute fmm2d
  mip load fmm2d
  ```
- **A package with dependencies.** `surfacefun` depends on `chebfun`; mip pulls both:
  ```
  mip install --channel flatironinstitute surfacefun
  ```
- **Pin a version.** `chebfun@5.7.0` requests a specific release:
  ```
  mip install chebfun@5.7.0
  ```
- **Use a fully qualified name.** Instead of `--channel`, name the channel inline:
  ```
  mip install flatironinstitute/flatironinstitute/flam
  ```

## Limitations to keep in mind

- Packages without a `numbl_wasm` (or `any`) build still install, but the compiled MEX functions they ship for other architectures won't run here. Calling them will error.
- Some MATLAB built-ins are not yet implemented in numbl. See [numbl differences from MATLAB](https://numbl.org/docs/differences).
- All state lives in browser memory. Refreshing the page resets the install set and the workspace.

## Learn more

- [mip documentation](https://mip.sh/docs)
- [numbl documentation](https://numbl.org/docs)
- [numbl-embed-example](https://github.com/magland/numbl-embed-example): how the embed works
