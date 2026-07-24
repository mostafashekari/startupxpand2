# Startup Xpand Android

Android application for Startup Xpand, built with Next.js, TypeScript, Capacitor and Kotlin.

## User experience

- English, Turkish and Arabic
- RTL support for Arabic
- Offline draft and retry queue
- Native sharing, network awareness, haptics and Android status-bar integration
- Responsive light and dark themes
- Adaptive, round and themed launcher icons generated from the final brand logo

## Brand logo

The source logo is stored as Base64 text in `brand/logo-source.base64`. Run:

```bash
python3 scripts/generate-brand-assets.py
```

This generates the in-app logo, splash artwork and all Android launcher icon densities without committing generated binary files.

## Android build

GitHub Actions generates the Capacitor Android project, builds release and preview APKs, aligns the release package and publishes the build files as a workflow artifact.

Private production signing material is intentionally not committed to this public repository.
