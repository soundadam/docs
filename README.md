# soundadam docs

Public documentation for soundadam products. This repository is the
intended Git source for Mintlify. Do not point Mintlify at
`soundadam/platform-gitops`.

| Directory | Product | Origin |
| --- | --- | --- |
| [`llm/`](llm/) | C-end API (NewAPI) | `https://llm.soundadam.com` |

WordPress (`https://soundadam.com`) stays the studio site and
`/pricing/` CTA. Lab keys stay on `https://llm2.soundadam.com` and are
not documented here.

## Mintlify

The C-end site lives entirely under `llm/` (`docs.json` is in that
folder, not the repository root). In the Mintlify dashboard:

1. Connect GitHub App access to **this repository only**.
2. Set the docs subdirectory to `llm`.
3. This tree deploys to https://soundapi.mintlify.app. Do not add
   `docs.soundadam.com` or `docs.llm.soundadam.com` to cluster
   `public-origin-tls`. A custom domain is a DNS CNAME to Mintlify,
   not a cluster SAN.

Local preview and checks:

```sh
cd llm
npx mint dev
npx mint validate
npx mint broken-links
```

GitHub Actions on this repository run `mint validate` and `mint broken-links`
from `llm/`. Connecting the Mintlify GitHub App is a separate dashboard
step; the workflow does not deploy.

## NewAPI copy

Until GitOps is switched, NewAPI still PUTs `About` /
`legal.user_agreement` / `legal.privacy_policy` from
`platform-gitops` `apps/new-api/reconcile/docs/`. The files in `llm/`
are the same text, hosted for the public docs site. Do not edit only
one copy and leave the other stale.
