# MedSim UX principles (v0.5)

## Navigation
One task at a time. The mobile bottom bar has five primary views. The remaining sections use More. No implicit login; Settings and Studio are local only.

## Patterns
Desktop: responsive grid to modal. Mobile: responsive two-column grid with multiple independent expandable recipes immediately after their cards. Each recipe contains Steps, Verification, and Notes. Distinguish working reports from verified native .hnx resources.

## Playground
One active demo at a time. Show current mock state prominently, controls beneath, latest action in one line, complete history on demand. Simulated data is never real clinical data.

## Impact, scenario, architecture
Tabs keep each view bounded and scannable. Keep current results and next action visible.

## Settings
Local visual preferences are separate from content and publication. Per-device IndexedDB/localStorage only, with export. Owner-only remote editing needs a protected write API and GitHub App with reviewed PRs; do not put tokens or shared passwords in client code.

## Known limits
Browser test environment blocks HTTP navigation and native persistent storage; tests use inline document and simulated localStorage with reload check. Validate on a real hosted origin and devices before merging.