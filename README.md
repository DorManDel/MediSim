# MediSim

A reusable simulation workflow pattern library and visual documentation studio for SimDesigner / LLEAP.

## Status

Initial repository. The browser-first prototype is being reviewed on a feature branch; it is **not** yet a production simulator integration or a published editing backend.

**Security:** Do not commit patient-identifying data, confidential institution information, or unauthorized clinical screenshots. Never commit GitHub tokens or credentials.

## Proposed architecture

- Static public knowledge site
- Local-first editor using IndexedDB and exportable images
- Optional GrapesJS design experiment
- Future protected authoring API (Cloudflare Access + GitHub App) that opens draft Pull Requests, with mobile approval before publishing

See the prototype pull request for implementation and caveats.
