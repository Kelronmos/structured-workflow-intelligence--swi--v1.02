# SWI V1.03 API Foundation

The SWI V1.03 API Foundation (Rust/Axum) has been successfully generated.

## Folder Structure

- `apps/api`: The Rust Axum API gateway implementation.
- `crates/`: The core logic broken into domain-specific crates (`swi-core`, `swi-workflow`, `swi-governance`, `swi-memory`, `swi-events`, `swi-security`, `swi-types`).
- `packages/sdk`: TypeScript SDK for frontend integration.
- `config/`: Configuration files (`development.toml`, `production.toml`, `security.toml`).
- `docs/`: Technical specifications (`api-spec.md`, `architecture.md`, `governance-model.md`).
- `tests/`: Integration and API test stubs.

## Usage

To run the Rust API locally:

```bash
cd apps/api
cargo run -p api
```

The API will listen on `0.0.0.0:3001` as configured.

Note: In the AI Studio environment, your primary entry point remains `server.ts` (Express) running on port `3000`, which already implements the `ApiResponse<T>` envelope contract to ensure seamless integration with the frontend!
