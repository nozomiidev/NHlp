# NashHash — Website

**Autonomous systems. Human terms.**

[NashHash](https://nashhash.dev/) is an independent AI systems and trust engineering studio in Japan. This repository contains the English-first, Japanese-localized corporate website, hosted on GitHub Pages.

## What we are building

- **Local-first personal agent app (in development):** resource-aware autonomous assistance for everyday smartphones; device-based execution, user-controlled tool permissions and optional remote reasoning are design priorities.
- **Field-tested agent trust protocols:** signature-based key-continuity handshakes (v0.2) and signed-post markers (v0.1) are in community field use; two independent end-to-end marker checks and seven key-verified agent counterparts are documented in project notes. Trust Receipts v0.3 remains in design. Reusable SDKs/hosted services are not yet presented as shipped.
- **Delegation and evidence infrastructure (design stage):** machine-readable scopes, approval requirements, revocation and auditable actions.
- **Commercial engineering services:** custom agent systems, trust protocol design, systems integration, feasibility assessments, and technical support.

Technical research, project-reported field-test results and outstanding engineering questions: [PROTOCOLS.md](PROTOCOLS.md). Identity and marking have been exercised in community tests; Trust Receipts v0.3 is in design. The field testing is not a formal security audit or evidence of customers.

## Website features

- English by default and a Japanese toggle with optional preference persistence.
- Editorial light theme with licensed Unsplash photography, native scroll and progress indication.
- Responsive layouts, mobile navigation, animated method illustration, expanding service details and section reveal transitions.
- Reduced-motion preferences, semantic sections and headings, alt text, focus indicators, and keyboard-operable controls.
- Detailed diagrams of the four-step identity handshake, signed post marker and trust-receipt concept, plus an editorial field-validation narrative. Anonymous contributor feedback and verification outcomes are described without using agent names.
- Full business address shown in the Contact section as originally published in an earlier iteration of this repository.

## Photography

Free commercial-use images from Unsplash, used for editorial illustration, not actual product screenshots:

1. [White architectural structure with stairs and blue sky — Eduardo Gorghetto](https://unsplash.com/photos/white-architectural-structure-with-stairs-and-blue-sky-Y9uYq6aDHAU)
2. [Orange building with a rounded archway — Kellen Riggin](https://unsplash.com/photos/orange-building-with-a-rounded-archway-over-a-door-9Ldaaf6wLRk)
3. [Hand holding a smartphone — Lorin Both](https://unsplash.com/photos/a-hand-holds-up-a-smartphone-_Q5HFTpOvDI)
4. [Geometric architecture with stairs — wang binghua](https://unsplash.com/photos/modern-architecture-with-geometric-shapes-and-stairs-XLccZCUXqbw)

Usage: [Unsplash License](https://unsplash.com/license). Photos and fonts load from third-party CDNs.

## Site operations

- GitHub Pages serves the static `index.html` from the repository's configured source. The `CNAME` file specifies `nashhash.dev`.
- Verify DNS/HTTPS, external visibility, and that `contact@nashhash.dev` can actually receive mail.
- Keep business details, service scope and project statuses accurate. Key-possession verification does not establish legal identity. Community field results are reported project outcomes, not independent security certifications.
- If suitable anonymized source references or reproducible test fixtures can be released, add them as evidence to [PROTOCOLS.md](PROTOCOLS.md). Do not disclose contributor handles without permission.
- The documentation and diagrams are research explanations, not finalized security guarantees or legal agreements.

## Quality verification

Static reviews should check (1) truthful business positioning, (2) correct protocol scope and security boundaries, and (3) mobile layout, localization coverage and JavaScript/markup integrity. Desktop and phone browsers must be visually verified after deployment.