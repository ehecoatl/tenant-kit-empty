# Ehecoatl Tenant Kit Empty

This tenant kit defines the minimal versioned tenant baseline for Ehecoatl.

It does not define an application anymore. It only provides:

- the tenant-level `config.json`
- the `ehecoatlVersion` property
- basic shared HTTP middlewares
- basic shared WS middlewares

`config.json` is copied to the opaque tenant root (`tenant_{tenant_id}`) and patched with runtime tenant metadata when the tenant is created.

The Empty Tenant Kit is intended to be a clean tenant foundation. App definitions, app routes, app assets, app actions, and smoke-test examples belong to app kits, not to this tenant kit.

Kit structure:

- `config.json`
- `shared/app/http/middlewares/`
- `shared/app/ws/middlewares/`

## Tenant Config

The bundled `config.json` defines the minimal version contract for new tenants:

- `ehecoatlVersion`: expected Ehecoatl runtime version for this tenant kit

Additional tenant metadata such as `tenantId`, `tenantDomain`, routing mode, and app configuration may be injected or managed by the runtime, scanner, registry, or app-specific kits depending on the installed setup.

## Shared Middlewares

Shared tenant middleware code can live under:

- `shared/app/http/middlewares`
- `shared/app/ws/middlewares`

These folders provide tenant-level reusable middleware that can be used by apps installed into the tenant when the app does not ship its own local middleware implementation.

## Purpose

The `.ehecoatl` tenant runtime and operational structure, app roots, app routes, and application files are expected to be created or managed outside this minimal kit.

This keeps the Empty Tenant Kit focused on one responsibility:

> provide the smallest possible tenant baseline compatible with a given Ehecoatl runtime version.
