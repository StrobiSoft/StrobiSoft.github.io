# StrobiSoft Update Hub

Public, static, read-only-to-clients update index. GitHub Pages hosts manifests; approved installers are hosted on GitHub Releases. No Pepper or Tailscale access is required.

Paths: `updates/<product>/<platform>/<channel>/latest.json`.

## Release gate
- Build and test the application.
- Verify the approved FamilyMail banner is present in the compiled UI.
- Publish a release artifact to GitHub Releases.
- Compute its SHA-256 and verify the download.
- Sign the manifest with an offline-protected release signing key; clients must verify signatures, not merely hashes.
- Atomically update the stable manifest only after validation.
- Never publish secrets, credentials, private update channels or internal Pepper endpoints here.

The FamilyMail placeholder manifest is deliberately NOT a valid update. The existing client must be adapted to allow cross-host HTTPS release downloads and verify a signed manifest before production use. Do not point clients at this placeholder.

The eventual custom domain `updates.strobisoft.com` requires DNS and Pages domain configuration; currently use the existing GitHub Pages site path.
