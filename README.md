# MedSim Toolkit v0.4 — Visual Authoring Prototype

A static, local-first documentation and design prototype for reusable Laerdal SimDesigner / LLEAP simulation workflows. No simulator connection, remote write access, account system, or production publishing endpoint has been implemented.

## Open

- `index.html`: knowledge hub, Scenario Logic demo, field evidence, reusable patterns, and **Studio** in the left navigation.
- `design-lab.html`: experimental GrapesJS drag-and-drop editor (requires access to pinned GrapesJS and Bootstrap CDN assets). A network connection is required for this page unless vendor assets are bundled.
- `content/knowledge.json`: versioned example public content loaded when served via HTTP(S), overridden by local draft in the same browser.

Serve locally with `python -m http.server 8000`, then visit `http://localhost:8000`. Opening `index.html` directly also works for the local sample, though fetching `content/knowledge.json` requires HTTP(S).

## How editing works

1. Open Studio → Edit Mode to add text, note, screenshot, warning or impact blocks.
2. Select a block to edit Markdown, status, source, width, or screenshot. Reorder via drag/drop (desktop) or up/down controls (mobile).
3. Switch Desktop/Tablet/Mobile preview; it changes the content-stage width and uses container queries.
4. Your private local draft and pictures are saved in IndexedDB if browser policy allows. **Save Draft is local to the current browser/profile**; it is not a remote save or an authorization system.
5. `JSON + images` exports a backup including images. Import restores that backup in a browser.
6. `Preset Code` exports a compressed/copyable text-and-layout schema, without binary media. Its 8-hex FNV check detects accidental damage; it is not a security signature.
7. `Publish ZIP` exports `content/knowledge.json` and `assets/*` for manual commit to a hosting repository. The browser cannot safely write to GitHub using an exposed credential.
8. In `design-lab.html`, experiment with free drag/resize and Bootstrap components. `Export JSON` contains the native GrapesJS editing project, whereas HTML is a preview/export artifact.

## Planned production workflow

**Public GitHub Pages/Cloudflare Pages** → **owner-only Cloudflare Access-protected Worker** → **GitHub App installation token stored only in Worker secrets** → **draft Pull Request** → **CI content and URL validation** → **owner approval on mobile** → **merge/deploy**.

- Cloudflare Access must validate every write request, not just hide Edit Mode in the frontend. Worker must enforce editor identity, CSRF defenses, file type/size limits, allowed destination paths, rate limits, and audit logs.
- Prefer GitHub App short-lived installation tokens rather than long-lived personal access tokens. Never ship a token in JavaScript, localStorage or a public repository.
- The work PC only needs access to the public site and protected publishing API; it need not open GitHub itself. Workstation and organization policies must permit this workflow.
- No login, GitHub push, CI-based publish or phone approval UI is live in v0.4.
- Because the repository is public, **never publish real patient data, internal institution details, or copyrighted clinical screenshots without permission and redaction**.

## Evidence status

`Reported working` means the user described successful field behavior; `Documented` means a source was reviewed; `Verified in LLEAP` must be selected only after actual retesting with simulator model, software version and evidence. The browser mocks are not simulator verification.

## Dependency policy

The main toolkit works without external JavaScript libraries. The optional design lab uses GrapesJS open-source v0.22.13 and Bootstrap v5.3.3 from CDN; for restricted workplace browsers, self-host pinned vendor files with license notices after IT/security approval.

For WebForge, isolate `design-lab.html` as an experimental rendering engine, but keep the medical pattern schema and evidence workflow separate from the generic editor core.