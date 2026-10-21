# Slides release site

Published static releases and authoring resources for Beta Mobility's Slides application.

Status: active generated repository. Public entry point: [slides.betamobility.ai](https://slides.betamobility.ai/). Static origin: [beta-slides-site.pages.dev](https://beta-slides-site.pages.dev/).

## Source and ownership

Application code, templates, the deck store and release tooling are maintained in [betamobility/slides](https://github.com/betamobility/slides). This repository contains the resulting HTML shells, signed release manifests, templates, agent guides and skill downloads. It is not the development checkout or the store for users' decks.

The deck-store Worker owns `slides.betamobility.ai` and fetches public release files from the Cloudflare Pages origin. Its authentication, deck storage and relay services are configured in the source repository, not here.

## Setup and deployment

No package installation, application build or runtime environment variables are required here. For development, clone the source repository and follow its [README](https://github.com/betamobility/slides#readme). Set `BENTO_SITE_DIR` there to this published checkout before assembling a release.

The source repository's `scripts/release.mjs` seeds generated output from the existing published tree, then replaces the artifacts it builds. `scripts/publish-site.mjs` mirrors that output and pushes it here. Publishing to GitHub alone does not deploy Cloudflare Pages: the documented release procedure then performs a direct upload to project `beta-slides-site` using Wrangler. Follow the source release procedure; do not rebuild or re-sign release artifacts by hand in this repository.

Cloudflare deployment credentials remain in Wrangler's authenticated environment or the approved secret store. There are no application secrets to place in an `.env` file here.

Keep this notice in the published tree when releasing. Changes to source ownership or hosting should update this file and the source repository's deployment documentation together.
