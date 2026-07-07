# Truth Kernel Methodology

A Truth Kernel contains only components whose behavior can be demonstrated, replayed, audited, and independently verified. Anything else becomes an extension.

The core question driving this architecture is:
**"If every UI element disappeared tomorrow, what remains that can still prove governance occurred?"**

That remainder is the **Truth Kernel**.

## Structural Assessment & Trust Boundaries

SWI separates system components into explicit trust boundaries. We mandate strict cryptographic honesty tagging (`SIMULATED`, `PARTIAL`, `VERIFIED`) to distinguish between prototype visualizations and actual cryptographic enforcement.

### Layer 0 — Decorative Layer (SIMULATED)
These components may be useful but provide no governance proof.
- Animated boot loaders
- Progress bars
- Dashboard metrics
- Status lights
- Mock TPM displays
- System readiness indicators
- AI Court visualizations without enforcement
- Governance certificates generated from simulated states

*Remove these, and governance should still function. If governance stops working when these disappear, the architecture is inverted.*

### Layer 1 — Governance Narrative Layer (PARTIAL)
Provides explanation but not enforcement.
- Policy descriptions
- Governance reports
- Roadmaps
- Compliance mappings
- Certification PDFs
- Vision documents
- Architecture diagrams

*These describe governance. They do not perform governance.*

### Layer 2 — Execution Governance Layer (PARTIAL/VERIFIED)
This is where truth begins.
- PolicyEngine
- ExecutionGate
- DecisionRecord
- RiskEvaluator

Can they independently accept requests, evaluate policy, and produce a deterministic outcome? 
If yes: **PARTIAL**. 
If every decision is replayable and produces identical output: **VERIFIED**.

### Layer 3 — Deterministic Event Kernel (VERIFIED)
This is SWI's strongest cryptographic core candidate.
- Kernel
- ReplayValidator
- HashChain
- StableStringify
- EventStore

**Required properties:**
1. **Determinism:** Same input must always produce the same Decision. No exceptions.
2. **Replayability:** Given an Event ledger, another machine must reproduce the exact Hash and Decision.
3. **Auditability:** Every decision creates a Receipt (Hash, Timestamp, Policy Version, Decision).

### Layer 4 — Cryptographic Boundary (SIMULATED/PARTIAL/VERIFIED)
Actual cryptographic boundaries vs simulated claims.
- Simulated mock signatures = **SIMULATED**
- Standard Ed25519/ECDSA with actual verification = **PARTIAL**
- Signatures strictly validated, chained, and enforced before execution = **VERIFIED**

### Layer 5 — Trust Anchor Layer (SIMULATED / PARTIAL / VERIFIED)
Hardware attestation boundaries: TPM, Secure Enclave, HSM, TrustZone.
Cannot attest state independently = **SIMULATED**

---

## Actual Trust Boundary Map

A decomposition of the SWI architecture based on cryptographic truth:

```
┌──────────────────────┐  <- UI / Dashboard
                             (Can Fail)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Policy Engine
                             (Can Fail)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Execution Gate
                             (Can Fail)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Deterministic Kernel
                             (Must Prove Truth)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Event Ledger
                             (Must Be Intact)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Crypto Layer
                             (Must Enforce Truth)
└──────────┬───────────┘
           ▼
┌──────────────────────┐  <- Hardware Trust
                             (Root of Truth)
└──────────────────────┘
```

Everything above the kernel can fail. The kernel must still prove what happened.

## Proposed Truth Kernel v1 Architecture

SWI has been structurally corrected around a minimal, deterministic **Truth Kernel**. It strips non-verifiable components out of the core trust loop.

The Truth Kernel implements only:
1. **Request**
2. **Policy Evaluation**
3. **Decision**
4. **Receipt**
5. **Hash Chain**
6. **Replay Validation**

### Kernel API

```typescript
interface TruthKernel {
  evaluate(request): Decision;
  record(decision): Receipt;
  replay(receipt): ReplayResult;
  verify(receipt): VerificationResult;
}
```

### Receipt Structure

```typescript
interface Receipt {
  receiptId: string;
  requestHash: string;
  decisionHash: string;
  policyVersion: string;
  timestamp: string;
  previousReceiptHash: string;
  signature?: string;
}
```

### Verification Rules
A receipt is valid **only** if:
- Hash chain is valid.
- Policy version exists.
- Replay matches deterministically.
- Cryptographic signature is valid.
Otherwise: **INVALID**.

Any component that cannot produce or verify a receipt is **not** part of the governance core. This rule eliminates architectural drift and makes every future feature justify its existence against a verifiable trust boundary.
