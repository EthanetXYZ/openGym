# openGym + Cloudflare Access builds

This branch only holds the build workflow. The code lives on
[`feat/mobile-cloudflare-access`](../../tree/feat/mobile-cloudflare-access)
(upstream PR [DuarteSantos8/openGym#439](https://github.com/DuarteSantos8/openGym/pull/439)).

Daily, `.github/workflows/cf-access-build.yml` takes the latest upstream release, applies that
branch on top, and publishes:

- **APK**: a [Release](../../releases) on this fork. Install and update with Obtainium.
- **API image**: `ghcr.io/ethanetxyz/opengym-api:cf-access`. Use it in place of
  `ghcr.io/duartesantos8/opengym-api:latest`; keep the official `opengym-web` image.

Needs one secret, `DEBUG_KEYSTORE_B64`: the base64 of the keystore the installed APK was signed
with, so every build installs over it.

Once the PR is merged upstream, switch back to the official APK and images and disable this
workflow.
