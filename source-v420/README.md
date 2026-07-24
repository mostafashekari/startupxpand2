# Startup Xpand v4.2.0 source restoration

The canonical private source snapshot is:

- File: `Startup-Xpand-v4.2.0-source.tar.gz`
- SHA-256: `a9f8b7dad8fef45cddc8eed754884478f5147063628b609eb5f3e4ce2b81e2e0`

It is included in the private developer handoff ZIP delivered with release 4.2.0. Extract it into a clean working directory before development:

```bash
sha256sum -c Startup-Xpand-v4.2.0-source.tar.gz.sha256
tar -xzf Startup-Xpand-v4.2.0-source.tar.gz
cd startup-xpand-v420-source
npm install
npm run typecheck
npm run build
```

Expected source checks:

- `app/page.tsx` preserves the approved v3.1 interface.
- `app/articles.ts` contains 399 entries for each of `en`, `tr` and `ar`.
- `public/articles-addon.js` uses `PAGE_SIZE = 20`.
- `public/articles-addon.css` contains the responsive pagination and article-reader styles.
- Android package id remains `com.startupxpand.app`.

Do not add the private signing bundle, secret environment file, passwords or GitHub token to this public directory.