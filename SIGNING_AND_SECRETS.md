# Android release signing and GitHub Secrets

Never commit a release keystore, passwords, Personal Access Tokens, populated `.env` files, or signing property files to this public repository.

## Required GitHub Actions Secrets

- `ANDROID_KEYSTORE_BASE64` — Base64 representation of the PKCS#12 release keystore
- `ANDROID_KEYSTORE_PASSWORD` — keystore password
- `ANDROID_KEY_ALIAS` — release key alias
- `ANDROID_KEY_PASSWORD` — private-key password

Linux encoding example:

```bash
base64 -w 0 startup-xpand-release-v4.p12
```

Paste the output directly into the repository secret. Do not save it in source control or workflow logs.

GitHub Actions provides a temporary `GITHUB_TOKEN` automatically. Developers who need a Personal Access Token should create a fine-grained, minimum-permission token with an expiry date and store it in a password manager. A live PAT must never be placed in a ZIP archive, APK, commit, issue, chat message, or backup distributed to other people.

Before every release, verify that the signing certificate matches the certificate used for previous versions. Losing the original release key can prevent Android from accepting future updates under the same application identity.
