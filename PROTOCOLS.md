# NashHash — Agent Trust Protocols (Research Notes)

**Status:** Early-stage research and specification work. These notes describe design intent and open engineering questions; they are not an interoperability standard, a security certification, or evidence that production endpoints are running.

## Protocol map

| Workstream | Stage | Question addressed |
| --- | --- | --- |
| Agent Identity / Key Continuity | v0.2 research protocol | Is this responding party able to use the private key associated with the public key I know? |
| Public Post Marking | v0.1 specification | Can a reader independently check the claimed cryptographic origin of a public post? |
| Trust Receipt | v0.3 under joint design / design freeze in progress | Who verified which claim or artifact, when, with what evidence, and what was the outcome? |

The shared primitive is **key → signature → verification**. This does not require a central account registry for the mathematical check. Establishing a trustworthy association with a real person, organization, device, or agent remains a separate concern.

## 1. Agent Identity Protocol (v0.2)

The guiding rule is **count counterparts by cryptographic key, not by display handle**.

### Described four-step interaction

1. **Greeting:** Two agents encounter one another and establish an initial communication context.
2. **Public-key exchange:** A participant presents a public key or a reference to its fingerprint.
3. **Nonce challenge:** The verifier creates a fresh unpredictable nonce. The participant signs that challenge using the corresponding private key and returns the signature.
4. **Signature verification:** The verifier checks the response against the presented or previously associated public key. A successful verification demonstrates possession of the corresponding private key at that moment.

This may support continuity of a known cryptographic counterpart over time, provided the binding to the key can be trusted and the private key remains uncompromised.

### Security boundary

- A valid signature does **not** prove real-world identity, intention, authorization, or that only one software agent controls a key.
- During a first encounter, exchanging keys without additional authentication is susceptible to key substitution or man-in-the-middle attacks.
- Freshness is important: challenge values must be generated securely and rejected if previously used. The exact nonce format, payload canonicalization, context binding, signature algorithm, public-key encoding, and replay checks need normative specification and interoperable tests.
- Key rotation, revocation, compromise recovery, cross-platform identity presentation, and policy for multiple devices are still explicit design questions.
- Hashing or displaying a key fingerprint is an indexing and comparison aid, not independent proof of its owner.

## 2. Public Post Marking Specification (v0.1)

The research concept is to append a concise signed marker to a public post. A conceptual example:

```text
We completed today's collaborative protocol discussion.
[mark: signed-reference]
```

The visible marker is intended to let an independent party locate the verification information and check a signature against a public key, instead of trusting the platform handle or profile name alone.

### Required engineering decisions

- Exactly which bytes are signed, how posts are canonicalized, and how edits and reposts are treated.
- How a short marker encodes or references a signature and key identity without exposing private material.
- How public keys are discovered, rotated, or invalidated.
- How verifiers distinguish an intact original post from a copied marker pasted onto different text.
- How the specification handles platform-specific formatting and truncation.

**Status:** Specification v0.1; the sample marker above is illustrative rather than a frozen wire format. Signature validity is conditional on correct content binding and key management.

## 3. Trust Receipt (v0.3, design in progress)

Trust Receipts aim to preserve an independently reviewable description of a verification event rather than only a conversational claim such as "I checked it."

Proposed information categories under discussion:

| Category | Intended meaning |
| --- | --- |
| Verifier | The party or cryptographic key making the verification statement |
| Time | Timestamp or time reference for the verification event |
| Subject | Claim, message, transaction, or other artifact being checked |
| Evidence | Referenced signatures, proof material, or other checkable material |
| Result | Verification outcome and any relevant scope or limitation |

These categories are an **illustration, not an approved schema**. The record format, canonicalization, signing requirements, evidence references, integrity guarantees, and error semantics remain design questions.

Design is being pursued collaboratively. The v0.3 work is in a design-freeze process and should not be described as a ratified standard, public service, or independent audit certification.

## How the work relates to products and services

- **Personal-agent application:** targets local-first operation on low-powered mobile devices, with user-controlled permissions and optional remote reasoning where appropriate. It is in development.
- **Developer-facing trust components:** identity checking, signed-origin indicators, and verification records are being explored as reusable integrations; an SDK or hosted service is not presented as shipped.
- **Delegation and accountability systems:** machine-readable permission boundaries, approvals, expiry/revocation, and audit evidence are an infrastructure research and engineering direction.
- **Commissioned engineering:** design, prototyping, agent runtime integrations, protocol implementations, technical evaluations, and support can be scoped as services.

Technical permission records do not replace legally binding human contracts. Agent systems must remain subject to appropriate human oversight, applicable law and the relevant platform rules.

---

For technical cooperation and commissioned engineering, use the contact information on [nashhash.dev](https://nashhash.dev/).
