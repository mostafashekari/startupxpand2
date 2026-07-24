# Release signing and GitHub Secrets

Do **not** commit a release keystore, passwords, access tokens, or populated `.env`/properties files to this public repository.

Configure these repository Actions Secrets for signed release builds:

- `ANDROID_KEYSTORE_BASE64`: Base64 representation of the PKCS#12 release keystore
- `ANDROID_KEYSTORE_PASSWORD`: keystore password
- `ANDROID_KEY_ALIAS`: signing key alias
- `ANDROID_KEY_PASSWORD`: private-key password

Linux example for encoding the keystore:

```bash
base64 -w 0 startup-xpand-release-v4.p12
```

Paste the result directly into the GitHub Actions Secret. Do not save the encoded value in the repository.

GitHub automatically provides an ephemeral `GITHUB_TOKEN` to workflows. Human developers who require a Personal Access Token should create a fine-grained token with minimum permissions, an expiry date, and storage in a password manager. Never place a live token in source archives, APKs, issues, commits, workflow logs, or handoff documents.

The release certificate fingerprint should be checked before publishing every update. Losing the original release key may prevent Android from accepting future updates under the same application identity.
