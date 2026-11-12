# Sub-Store Surge VLESS

An unofficial Sub-Store build adding import and output support for Surge's native VLESS format.

## Install in Surge

Add this custom module:

`https://raw.githubusercontent.com/ByteValley/sub-store-surge-vless/main/Surge-Sub-Store-VLESS.sgmodule`

The module loads its VLESS-enabled core script from:

`https://raw.githubusercontent.com/ByteValley/sub-store-surge-vless/main/sub-store-1-vless.min.js`

Use this module in place of the official Sub-Store Surge module so only one module handles `sub.store` requests. The Sub-Store web interface can remain the same. This package does not require deploying the full Node/Docker backend.

## Files

- `Surge-Sub-Store-VLESS.sgmodule`: custom Surge module.
- `sub-store-1-vless.min.js`: compiled module script.
- `sub-store-surge-vless.patch`: patch against the upstream source revision below.
- `sub-store-surge-vless-package.zip`: package with the modified source files, README, and AGPL-3.0 license.

## Supported VLESS combinations

- RAW/TCP: no TLS, TLS, or REALITY; Vision flow with TLS or REALITY.
- WebSocket: no TLS or TLS, including path and headers.
- gRPC: TLS or REALITY, including service name, mode, and authority.

Surge requires iOS 6.0.0+ or Mac 6.12.0+. XHTTP, HTTPUpgrade, mKCP, and VLESS Encryption are unsupported by Surge's native VLESS implementation.

## Source and build

Base repository: [sub-store-org/Sub-Store](https://github.com/sub-store-org/Sub-Store)  
Base revision: `d8fc0e69a7f472485d338049b85d20d3f44b41a5` (Sub-Store 2.44.7)

Rebuild from that revision by applying `sub-store-surge-vless.patch`, then run `pnpm install --frozen-lockfile` and `pnpm bundle:esbuild` in `backend/`. The module bundle is generated at `backend/dist/sub-store-1.min.js`.

Bundle SHA-256: `9c485e7220a4bace655bba2cd58798598dbe26ef5df86bf3a903e5715e7c251c`
