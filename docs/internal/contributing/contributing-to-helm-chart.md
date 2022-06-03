# Contributing to the Grafana Mimir Helm Chart

## Differences to general workflow

- The workflow is tailored to the helm chart.
- Changelog is in a the chart itself [operations/helm/charts/mimir-distributed/CHANGELOG.md](https://github.com/grafana/mimir/blob/main/operations/helm/charts/mimir-distributed/CHANGELOG.md).
- Version is set in the chart itself [operations/helm/charts/mimir-distributed/Chart.yaml](https://github.com/grafana/mimir/blob/main/operations/helm/charts/mimir-distributed/Chart.yaml).

## Workflow

Grafana Mimir Helm Chart follows a standard GitHub pull request workflow. If you're unfamiliar with this workflow, read the very helpful [Understanding the GitHub flow](https://guides.github.com/introduction/flow/) guide from GitHub.

You are welcome to create draft PRs at any stage of readiness - this
can be helpful to ask for assistance or to develop an idea. But before
a piece of work is finished it should:

- Be organised into one or more commits, each of which has a commit message that describes all changes made in that commit ('why' more than 'what' - we can read the diffs to see the code that changed).
- Each commit should build towards the whole - don't leave in back-tracks and mistakes that you later corrected.
- Bump the version of the chart, see [Versioning](#versioning) bellow.
- Include a [CHANGELOG](./README.md#changelog) message in [operations/helm/charts/mimir-distributed/CHANGELOG.md](https://github.com/grafana/mimir/blob/main/operations/helm/charts/mimir-distributed/CHANGELOG.md).

## Versioning

On the `main` branch, versions should be _pre-release_ only, meaning that the version should be suffixed by `-beta.<n>`, for example `2.1.0-beta.1` for a pre-release of the next stable `2.1.0` chart version. Versioning should follow the [Helm3 standard](https://helm.sh/docs/topics/charts/#charts-and-versioning) which is [SemVer 2](https://semver.org/spec/v2.0.0.html).

Maintainers will create regular stable releases by cherry picking commits from the `main` branch to a release branch (e.g. `release-2.1`).

## Documentation

After updating the version, please run [helm-docs](https://github.com/norwoodj/helm-docs) to generate [operations/helm/charts/mimir-distributed/README.md](https://github.com/grafana/mimir/blob/main/operations/helm/charts/mimir-distributed/README.md) from its template.

## Using beta version

Once a PR is merged to `main`, it takes a couple of minutes for it to be published in [https://grafana.github.io/helm-charts](https://grafana.github.io/helm-charts) Helm repository.

In order to search, template, install, upgrade, etc beta versions of charts, Helm commands require the user to specify the `--devel` flag. This means that checking for whether the beta version is published should be done with `helm search repo --devel`.
