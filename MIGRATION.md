# Migration to novidades-platform

Status: **Planned / source preserved**

Target repository:
`atlashub-digital/novidades-platform`

## KEEP / migrate concepts

### Protected asset delivery
Preserve:
- private asset storage;
- short-lived signed delivery;
- server-side authorization before signing assets.

Target:
- R2 for scalable object delivery where appropriate;
- ARO entitlement is authoritative.

### Structured online content
Preserve:
- content blocks/modules;
- protected Reader concept;
- release/version discipline.

Target:
- `novidades.content_items`;
- `content_releases`;
- `content_modules`;
- `content_lessons`.

### Product packaging knowledge
Preserve selected copy, deliverable definitions and product-learning from the first digital releases only after current content/rights revalidation.

## REMOVE from target

### Direct checkout
Current:
`src/app/api/checkout/route.ts` → XPAYMENTS directly.

Target:
Novidades → ARO `POST /v1/checkout-sessions`.

### Provider webhook
Current:
`src/app/api/webhooks/xpayments/route.ts`.

Target:
provider webhooks terminate inside ARO. Novidades consumes signed ARO project events and resolves authoritative entitlements through ARO.

### Local entitlement authority
Current:
`digital_entitlements` determines access.

Target:
ARO `/v1/entitlements/resolve` determines access. Novidades may keep a read projection/cache only when contractually safe.

### Claim-token library
Current:
reference + claim stored/recovered on the browser.

Target:
authenticated customer identity + server-side entitlement resolution.

## Archive process

Do not delete this repository until:
1. unique useful code/assets are migrated;
2. canonical platform passes preview/E2E;
3. no production DNS/deployment points here;
4. historical customer access is preserved/reconciled;
5. explicit archive GO is given.

After that:
- archive repository;
- keep Git history;
- remove deploy hooks/secrets;
- document final migration SHA/PR.
