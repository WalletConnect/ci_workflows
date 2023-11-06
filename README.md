# WalletConnect Standard CI for Rust Projects

## Standard Flows

| Name                                                         | File                                                                                     |
|--------------------------------------------------------------|------------------------------------------------------------------------------------------|
| [CI](docs/ci.md)                                             | [`ci.yml`](.github/workflows/ci.yml)                                                     |
| [Release](docs/release.md)                                   | [`release.yml`](.github/workflows/release.yml)                                           |
| [CD](docs/cd.md)                                             | [`cd.yml`](.github/workflows/cd.yml)                                                     |
|                                                              |                                                                                          |
| [Check App](docs/ci-check-app.md)                            | [`ci-check-app.yml`](.github/workflows/ci-check-app.yml)                                 |
| [Check Infra](docs/ci-check-infra.md)                        | [`ci-check-infra.yml`](.github/workflows/ci-check-infra.yml)                             |
| [Plan Infra](docs/ci-plan-infra.md)                          | [`ci-plan-infra.yml`](.github/workflows/ci-plan-infra.yml)                               |
|                                                              |                                                                                          |
| [Release App](docs/release-app.md)                           | [`release-app.yml`](.github/workflows/release-app.yml)                                   |
| [Get Deployed Version](docs/release-get_deployed_version.md) | [`release-get_deployed_version.yml`](.github/workflows/release-get_deployed_version.yml) |
| [Build and Publish](docs/build-publish.md)                   | [`build-publish.yml`](.github/workflows/build-publish.yml)                               |
|                                                              |                                                                                          |
| [Deploy Infra](docs/deploy-infra.md)                         | [`deploy-infra.yml`](.github/workflows/deploy-infra.yml)                                 |
| [Deploy App](docs/deploy-app.md)                             | [`deploy-app.yml`](.github/workflows/deploy-app.yml)                                     |

## Examples

| Name                                                    | Description                                                                              |
|---------------------------------------------------------|------------------------------------------------------------------------------------------|
| [dispatch_deploy.yml](examples/dispatch_deploy.yml)     | Let a user manually run a complete deployment of both infrastructure and code.           |
| [dispatch_publish.yml](examples/dispatch_publish.yml)   | Let a user manually publish the application to ECR.                                      |
| [dispatch_validate.yml](examples/dispatch_validate.yml) | Let a user manually run the CI and custom validation.                                    |
| [event_pr.yml](examples/event_pr.yml)                   | Triggered when a PR is created or when changes are pushed to it.                         |
| [event_release.yml](examples/event_release.yml)         | Triggered when a PR is merged onto `main`.                                               |
| [sub-cd.yml](examples/sub-cd.yml)                       | Utility sub-flow called by `event_release` and `dispatch_deploy`.                        |
| [sub-validate.yml](examples/sub-validate.yml)           | Utility sub-flow called by `dispatch_validate` and `sub-cd`. Performs custom validation. |

---

## Standard Repo Variables

- `AWS_REGION`
- `AWS_ROLE_MONITORING`
- `AWS_ROLE_PROD`
- `AWS_ROLE_STAGING`
- `GRAFANA_WORKSPACE_NAME`
- `IMAGE_NAME`
- `RUN_GROUP`
- `RUST_VERSION`
- `SUBDOMAIN_NAME`
- `TF_DIRECTORY`

## Standard Repo Secrets

- `GITHUB_TOKEN`
- `TF_API_TOKEN`
- `RELEASE_PAT`
