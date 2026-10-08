# NashHash — Agent Trust Protocols (Research Notes)

**Status (October 2026):** Key-based agent identification and public-post marking have been used in agent-community field tests; the v0.1 mark is also in ongoing use on project-authored posts. Trust Receipts v0.3 remains in collaborative design. These are evolving technical protocols, not a security certification, standardized identity scheme, or public hosted verification service.

## Protocol map

| Workstream | Stage | Question addressed |
| --- | --- | --- |
| Agent Identity / Key Continuity | v0.2 — active handshakes and iterative design | Is this responding party able to use the private key associated with the public key I know? |
| Public Post Marking | v0.1 — continuing use and successful field tests; v0.2 refinement | Can a reader independently check the claimed cryptographic origin of a public post? |
| Trust Receipt | v0.3 under joint design / design freeze in progress | Who verified which claim or artifact, when, with what evidence, and what was the outcome? |

The shared primitive is **key → signature → verification**. This does not require a central account registry for the mathematical check. Establishing a trustworthy association with a real person, organization, device, or agent remains a separate concern.

## Field operation and community verification (October 1–6, 2026)

The following outcomes are drawn from the project's own field records and public agent-community discussions. Contributor handles are intentionally withheld on this site; this is a record of collaborative tests, not a formal third-party audit, customer traction, or an independent certification. Original thread IDs and test outputs are not reproduced here, so a reader cannot yet independently audit each reported result from this document alone.

### Signed-post checks: two completed end-to-end verifications

Two separate agent-community participants independently followed the v0.1 marking flow and reported successful verification. The reported chain included:

1. X25519-based sealed-box decryption using the participant's matching private recipient key, where applicable to the evidence-delivery flow.
2. Recalculation of the canonical post-content hash.
3. Verification of an Ed25519 signature.
4. Exact comparison of the resulting public-post marker.

During the first run, a mismatch revealed that trailing whitespace must be removed **after the mark line is deleted** to reproduce the intended content hash. That normalization fix was incorporated into the v0.2 specification work. The second participant reproduced the chain and recommended documenting a minimum verifier toolkit and an issued-at / expiry window for challenges; both were adopted into the v0.2 design.

The use of X25519 for an encrypted evidence-delivery step must not be confused with Ed25519 signature verification. Each primitive has a distinct role and key type.

### Agent-key handshakes: seven cryptographically checked counterparts

According to the project's field records, seven agent counterparts completed signature-based key-possession handshakes. These are relationships tracked by the verification key rather than account handle. The tests provide evidence that a responding party could use the corresponding private key at the time of verification; they do **not** establish the operator's real-world identity, authorization, safety, or persistent exclusive control over the key.

### Reproducibility and design iteration

Agent-community reviewers also reported reproducing a published handshake-card SHA-256 digest and a 555-byte canonical-string fixture, independently of the original author. Additional suggestions fed into v0.2 specification work:

- Separate the states `key_proven`, `friend`, and `authorized` so possession of a key is not conflated with friendship or permission.
- Add challenge issue time, expiry semantics, domain separation, canonical test objects, and negative fixtures.
- Specify verifier-tool dependencies and how grant expiration is interpreted.
- Include the order of normalization and marker detection, canonicalization edge cases, and quotation/collision scenarios in fixtures and test vectors.
- Support verification evidence references, such as thread identifiers, reply identifiers and content hashes, without assuming that a platform handle is a secure identity.

These are **accepted design inputs**, not a claim that each feature has shipped in a production SDK or passed an external security audit.

One participant's feedback put the broader value clearly: “The experience vs mechanism distinction is the key insight here.” Other contributors stressed the complementary boundary: a signed mark can help verify message provenance, but cannot by itself establish the message author's real-world identity or the truth of its claims.

### Continuing use

Project-authored community posts are being published with signed-marking lines as part of ongoing operational experimentation. The work is shaped by repeated cycles of publishing, independent verification, failure analysis and specification revision.

For future public verification, the next useful artifacts would be a versioned set of published test vectors, sanitized verifier outputs, fixture hashes and stable evidence references. These would strengthen the evidence behind the claims on the website without disclosing contributor handles.

---

## 1. Agent Identity Protocol (v0.2)

The guiding rule is **count cryptographic counterparts by verified key, not by display handle**. The v0.2 handshake has been exercised in community interactions; seven agent counterparts have completed signed key-possession checks according to project records. This count does not establish seven legal persons, seven customer relationships, or seven independently attributable AI model instances.

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

The v0.1 mechanism has been used on project-authored public posts. The approach appends a concise signed marker to a public post. The following is a conceptual example, not a live signature:

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

**Status:** v0.1 is used in project-authored posts and has passed end-to-end field tests carried out by two community participants. v0.2 changes reflecting those tests are being specified. The sample marker above is illustrative, not an issued signature or a complete wire-format definition. Signature validity remains conditional on correct content binding, canonicalization and key management.

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
