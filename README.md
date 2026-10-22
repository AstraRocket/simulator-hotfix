# AstraRocket (hotfix)

**▶ [Launch the hotfix build](https://astrarocket.github.io/simulator-hotfix/)**

This repository publishes the **hotfix** build of [AstraRocket](https://github.com/AstraRocket/simulator), the browser-based UI for the OpenRocket engine. The hotfix site runs the `hotfix` branch of [AstraRocket/simulator](https://github.com/AstraRocket/simulator): what is live on the [production site](https://astrarocket.github.io/simulator/), plus urgent fixes being checked before they go there.

It has no new features. Those come through the [dev](https://astrarocket.github.io/simulator-dev/) and [beta](https://astrarocket.github.io/simulator-beta/) sites. A fix here reaches production only if it is judged worth shipping ahead of the next release.

There is no app source here. This repository exists because GitHub Pages gives each repository one site, so the hotfix build needs a repository of its own to publish to.

## Using the hotfix build

- **Use it to confirm a fix.** If you reported a problem and were pointed here, check whether it is fixed and say so on the issue. For everything else, use the [production site](https://astrarocket.github.io/simulator/).
- **Your data is kept apart from the other sites.** The hotfix build uses its own browser storage, so rockets, motors, materials and settings saved here do not show up on the production, dev or beta sites, and nothing you do here touches your production designs. To check a fix against one of your designs, export it as a `.ork` from production and import it here.
- **It can be installed separately.** The installed app, its name and its version are labeled hotfix, so it can sit beside the production install.
- **Version numbers name the build.** A hotfix version reads like `1.2.3-hotfix.45`, where the last number is the deploy run. Include it when reporting a problem.

## Reporting problems

Open an issue on [AstraRocket/simulator](https://github.com/AstraRocket/simulator/issues), not here, and include the version shown in the app.

## How the site is deployed

The build itself lives in the main repository, in [`.github/workflows/channel-deploy.yml`](https://github.com/AstraRocket/simulator/blob/hotfix/.github/workflows/channel-deploy.yml) on the `hotfix` branch. This repository's [`.github/workflows/deploy-hotfix.yml`](.github/workflows/deploy-hotfix.yml) only calls it, with `channel: hotfix`.

To publish the hotfix build:

1. Open **Actions → Deploy hotfix** in this repository.
2. Click **Run workflow**.

The called workflow checks out the `hotfix` branch of AstraRocket/simulator, builds the app and its docs with the `/simulator-hotfix/` base path and `APP_CHANNEL=hotfix`, and deploys the result to this repository's Pages site. Because a called workflow runs as its caller, the run, its Pages deployment and its token all belong to this repository; the main repository is only read. Nothing in the main repository can start this deploy, so it cannot publish over the production site.

### Setup

Pages for this repository must be set to deploy from **GitHub Actions** (Settings → Pages → Build and deployment → Source).
