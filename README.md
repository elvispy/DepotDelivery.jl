# DepotDelivery

[![Build Status](https://github.com/joshday/DepotDelivery.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/joshday/DepotDelivery.jl/actions/workflows/CI.yml?query=branch%3Amain)

<p align="center"><b>DepotDelivery</b> bundles a Julia project into a standalone depot that can run in air-gapped environments.</p>



## Features

- Bundles all necessary Julia code and artifacts needed to run without internet access.
- Build for platforms other than the host platform.

## Usage

```julia
using DepotDelivery

path = DepotDelivery.build_depot("Project.toml"; platform = Base.BinaryPlatforms.HostPlatform())
```

## Building for Non-Host Platforms

- To build for a non-host platform, provide any `Base.BinaryPlatforms.AbstractPlatform` as the `platform` argument.
- See [Julia's supported OS/architectures](https://www.julialang.org/downloads/index.html#supported_platforms).
- See `?Base.BinaryPlatforms.Platform` and the types in `Pkg.BinaryPlatforms` for details, e.g.

```julia
import Pkg

Platform("windows", "x86_64"; cuda == "10.1")

# `arch` argument must be in (:x86_64, :i686m, :armv7l, :armv6l, :aarch64, :powerpc64le)
Pkg.BinaryPlatforms.Windows(:x86_64)
Pkg.BinaryPlatforms.MacOS()
Pkg.BinaryPlatforms.Linux(:powerpc64le)
Pkg.BinaryPlatforms.FreeBSD(:armv7l)
```
