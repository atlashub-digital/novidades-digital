# Novidades Digital — Deprecated Runtime / Migration Source

> **Status: DEPRECATED AS AN INDEPENDENT APPLICATION**

The canonical Novidades.Store application is now:

`atlashub-digital/novidades-platform`

This repository is retained as a **migration source and historical implementation record**. It must not become a second production customer journey for the same Novidades catalog.

## Why this repository existed

The original architecture correctly proposed splitting digital delivery when the digital surface became independently deployable with:
- authenticated customer library;
- interactive tools;
- protected delivery;
- heavy media/course player;
- independent release cadence.

That condition occurred and this application was created.

The product strategy has since changed: **Novidades.Store itself is now digital-first**. Keeping a separate `novidades-digital` runtime would duplicate:
- product registry;
- checkout;
- payment state;
- entitlement;
- customer access;
- delivery;
- release governance.

Therefore the application boundary is being collapsed back into the canonical Novidades platform.

## What is useful here

Migration candidates:
- protected-delivery patterns;
- digital asset metadata;
- entitlement-aware UI concepts;
- checkout intent history/schema as migration evidence;
- online content release patterns;
- product packaging lessons.

## What must not be copied as target architecture

- direct XPAYMENTS integration;
- project-owned XPAYMENTS webhook;
- local payment-status authority;
- local entitlement authority;
- claim-token/localStorage as the final customer identity model;
- duplicate hard-coded product registry;
- duplicate static GitHub Pages deployment.

ARO is the target authority for checkout, order, payment state and entitlement.

## Migration

See `MIGRATION.md`.

No production deployment, DNS change or real payment is authorized from this branch.
