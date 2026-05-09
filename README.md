![Igloo Logo](./files/system/usr/share/pixmaps/fedora_logo_med.png#gh-light-mode-only)
![Igloo Logo](./files/system/usr/share/pixmaps/fedora_whitelogo_med.png#gh-dark-mode-only)

[![bluebuild build badge](https://github.com/jordanbrotherton/igloo/actions/workflows/build.yml/badge.svg)](https://github.com/jordanbrotherton/igloo/actions/workflows/build.yml)

Igloo is a cozy 'blank canvas' desktop, with tools. This is currently moreso a personal image, but with an aim to make it general for anyone.

## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

> [!NOTE]  
> If you are on an Nvidia system, replace `igloo` with `igloo-nvidia` for preinstalled drivers.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/jordanbrotherton/igloo:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/jordanbrotherton/igloo:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/how-to/generate-iso/#_top). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/jordanbrotherton/igloo
```
