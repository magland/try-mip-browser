<script src="https://numbl.org/numbl-embed.js"></script>

# Try mip in the browser

[mip](https://mip.sh) is a package manager for MATLAB. This page lets you try it in your browser without installing anything.

> **Runs on [numbl](https://numbl.org), not MATLAB.**
> numbl is like MATLAB but runs in the browser. mip commands behave the same way here as in MATLAB. The catch is that a package shipping compiled MEX for Linux, Mac, or Windows but no browser build will install fine and then fail when you actually call its compiled functions. Pure MATLAB packages work, and so do packages that include a `numbl_wasm` build.

## Try it

Type the commands below into the REPL. Anything you install and any variables you create stick around until you refresh the page.

<numbl-embed mode="repl">
<iframe width="100%" height="600" frameborder="0"></iframe>
</numbl-embed>

## A quick tour

### Help

```
help mip
```

For details on a single command:

```
mip help install
mip help avail
```

### List available packages

The default channel is `mip-org/core`:

```
mip avail
```

Or list packages from another channel, like the one Flatiron Institute publishes (`chunkie`, `finufft`, `fmm2d`, `flam`, `surfacefun`, ...):

```
mip avail --channel flatironinstitute
```

The list shows packages whose architecture is `numbl_wasm` (browser builds) or `any` (pure MATLAB).

### Install a package

`chebfun` is a library for working with functions numerically. It's pure MATLAB, so it installs cleanly here:

```
mip install chebfun
```

mip pulls the package and any dependencies into a virtual filesystem in your browser.

### Load it onto the path

```
mip load chebfun
```

Now you can use it:

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

You can also look at packages you haven't installed:

```
mip info --channel flatironinstitute chunkie
```

### Unload and uninstall

```
mip unload chebfun
mip uninstall chebfun
```

`mip uninstall` also removes any dependencies that were pulled in automatically and aren't needed by anything else.

## More to try

- A package with a browser MEX build. `fmm2d` (2-D fast multipole methods) has a `numbl_wasm` variant, so it works here:
  ```
  mip install --channel flatironinstitute fmm2d
  mip load fmm2d
  ```
- A package with dependencies. `surfacefun` depends on `chebfun`, and mip pulls both:
  ```
  mip install --channel flatironinstitute surfacefun
  ```
- A specific version:
  ```
  mip install chebfun@5.7.0
  ```
- A fully qualified name (channel built into the package name):
  ```
  mip install flatironinstitute/flatironinstitute/flam
  ```

## Limitations

- A package without a `numbl_wasm` or `any` build will install, but its compiled functions will error when you call them.
- numbl doesn't implement every MATLAB builtin yet. See [numbl differences from MATLAB](https://numbl.org/docs/differences).
- Everything lives in browser memory. Refreshing the page wipes installed packages and your workspace.

## Learn more

- [mip docs](https://mip.sh/docs)
- [numbl docs](https://numbl.org/docs)
- [numbl-embed-example](https://github.com/magland/numbl-embed-example) shows how the embed works.
