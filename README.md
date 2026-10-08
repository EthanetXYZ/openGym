# openGym + Cloudflare Access builds

This branch only holds the build workflow. The code lives on
[`feat/mobile-cloudflare-access`](../../tree/feat/mobile-cloudflare-access)
(upstream PR [DuarteSantos8/openGym#439](https://github.com/DuarteSantos8/openGym/pull/439)).

Daily, `.github/workflows/cf-access-build.yml` takes the latest upstream release, applies that
branch on top, and publishes:

- **APK**: a [Release](../../releases) on this fork. Install and update with Obtainium.
- **API image**: `ghcr.io/ethanetxyz/opengym-api:cf-access`. Use it in place of
  `ghcr.io/duartesantos8/opengym-api:latest`; keep the official `opengym-web` image.

The APK is a release build, app ID `ch.duartesantos.opengym.cf` ("openGym CF"), so it installs
beside the official app. Nothing is published unless upstream's frontend and API tests pass.

Needs two secrets: `RELEASE_KEYSTORE_B64` (base64 of the signing keystore, alias `opengym`) and
`RELEASE_KEYSTORE_PASSWORD`. Every build must be signed with that same key, or Android refuses
the update.

Once the PR is merged upstream, switch back to the official APK and images and disable this
workflow.
