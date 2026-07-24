# Secure developer continuity

## Files that belong outside Git

Keep these materials in an encrypted offline backup or a restricted password manager/secret store:

- Android release keystore (`startup-xpand-release-v4.p12`)
- Keystore and private-key passwords
- GitHub Actions signing values
- Original project backup
- Signed release APK and certificate verification reports
- Any GitHub Personal Access Token

Never place these files in a public branch, issue, pull request, Actions artifact, shared chat, or unencrypted cloud folder.

## GitHub Actions signing secrets

Configure these repository secrets when signed CI releases are needed:

- `ANDROID_KEYSTORE_BASE64`
- `ANDROID_KEYSTORE_PASSWORD`
- `ANDROID_KEY_ALIAS`
- `ANDROID_KEY_PASSWORD`

The private handoff ZIP includes `github/ACTIONS-SECRETS.private.env` with the Android signing values prepared from the release keystore. Import them into repository Actions Secrets, then keep or delete the plaintext file according to the project security policy.

## GitHub token

A connected-tool token is not exportable. Create a new fine-grained Personal Access Token only when needed, restrict it to `mostafashekari/startupxpand2`, grant minimum permissions, add an expiration date, and store it in a password manager. Revoke it immediately if exposed.

## Android update continuity

To keep future versions installable over the current app:

1. Preserve package id `com.startupxpand.app`.
2. Sign releases with the same release keystore.
3. Increase `versionCode` for every release.
4. Keep a verified offline copy of the keystore, certificate and passwords.
5. Validate APK signature, package id, version and SHA-256 before distribution.