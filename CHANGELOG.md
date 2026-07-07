# Changelog

## [1.0.0-rc1] - 2026-04-10

### Added
- **S9 Continuous Proof Pipeline**: Real-time evidence generation with Firefly/Merkle integration.
- **Adversarial Test Suite**: Automated stress testing for kernel bypass, replay attacks, and drift manipulation.
- **START_HERE.md**: Comprehensive guide for reviewers.
- **AUTHORITATIVE_RUNTIME_AND_POLICY.md**: Clear definition of the governance boundary.
- **Automatic Key Rotation**: Server now generates RSA keys on-the-fly if missing.

### Changed
- **Hardened Security**: Replaced weak string checks with RS256 JWT verification.
- **Reorganized Structure**: Moved core logic to `core/` and frontend to `app/`.
- **Reconciled Policy**: Unified root and core manifests into a single authoritative source.
- **Improved Versioning**: Set real version and build identifiers.

### Fixed
- **TypeScript Compliance**: Resolved numerous type mismatches and implicit `any` errors.
- **Dependency Resolution**: Fixed missing `@types/node` and other dev dependencies.
- **Security**: Removed private keys from the package and added them to `.gitignore`.

### Security
- **Private Key Removal**: `private.pem` is no longer shipped in the package.
- **Replay Protection**: Implemented `jti` tracking in the kernel.
- **Drift Enforcement**: Server-side calculation of drift scores.
