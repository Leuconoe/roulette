# Local patches

The tracked source stays aligned with upstream. The deployment workflow applies
`remove-ads.patch` before building the GitHub Pages site. The patch preserves the
upstream advertising implementation and overrides its entry points with no-op
functions, minimizing conflicts during upstream updates.

To preview the patched source locally:

```sh
git apply --check patches/remove-ads.patch
git apply patches/remove-ads.patch
yarn dev
```

Restore the upstream source after the preview:

```sh
git apply --reverse patches/remove-ads.patch
```

After merging or rebasing an upstream update, verify that the customization is
still applicable:

```sh
git apply --check patches/remove-ads.patch
```

If that check fails, resolve the changed upstream code first and regenerate the
patch from the updated source before deploying.
