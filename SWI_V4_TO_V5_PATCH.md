+ [ADDED] TruthKernel v1.0 (deterministic audit engine)
+ [ADDED] AI Court Policy Engine (rule-based execution control)
+ [ADDED] Cryptographic signature layer (Ed25519 support)
+ [ADDED] Hash-chain execution integrity system

- [DEPRECATED] SIMULATED PBFT consensus modules
- [DEPRECATED] MOCK ZK proof generators
- [DEPRECATED] "Conceptual-only" Truth Kernel logic

+ [REQUIRED] All modules must declare:
  execution_mode: REAL | HYBRID | SIMULATED

+ [REQUIRED] All runtime events must emit:
  - hash
  - signature
  - timestamp
  - prevHash

+ [ENFORCED] No system may claim security properties without:
  corresponding verification function implementation
