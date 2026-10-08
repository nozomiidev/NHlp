# NashHash — Website

**Autonomous systems. Human terms.**

[NashHash](https://nashhash.dev/) is an independent AI systems and trust engineering studio in Japan. This repository contains the English-first, Japanese-localized corporate website, hosted on GitHub Pages.

## What we are building

- **Local-first personal agent app (in development):** resource-aware autonomous assistance for everyday smartphones; device-based execution, user-controlled tool permissions and optional remote reasoning are design priorities.
- **Agent trust components (research/prototyping):** public-key challenge–response verification, signed-origin post markers and evidence-backed records for agent interactions.
- **Delegation and evidence infrastructure (design stage):** machine-readable scopes, approval requirements, revocation and auditable actions.
- **Commercial engineering services:** custom agent systems, trust protocol design, systems integration, feasibility assessments, and technical support.

Technical research and open engineering questions: [PROTOCOLS.md](PROTOCOLS.md). The v0.2 agent identity protocol, v0.1 public post marking specification, and v0.3 trust receipt design are **not presented as production-ready products**.

## Website features

- English by default and a Japanese toggle with optional preference persistence.
- Editorial light theme with licensed Unsplash photography, native scroll and progress indication.
- Responsive layouts, mobile navigation, animated method illustration, expanding service details and section reveal transitions.
- Reduced-motion preferences, semantic sections and headings, alt text, focus indicators, and keyboard-operable controls.
- Detailed research diagrams and explanations showing the four-step identity handshake, signed post marker, trust receipt concept, technical limits, development status and commercial service paths.
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
- Keep business details, service scope and project statuses accurate. Do not conflate cryptographic key possession with legal identity.
- The documentation and diagrams are research explanations, not finalized security guarantees or legal agreements.

## Quality verification

Static reviews should check (1) truthful business positioning, (2) correct protocol scope and security boundaries, and (3) mobile layout, localization coverage and JavaScript/markup integrity. Desktop and phone browsers must be visually verified after deployment.