# CI

`ci.yml`

Check the validity of the infrastructure and application code without modifying the environments.

```mermaid
graph LR
    START((Start))
    check_infra[[Check Infra]]
    plan_infra[[Plan Infra]]
    check_app[[Check App]]
    END((End))
    START --> check_infra
    START --> check_app
    check_infra --> plan_infra
    check_app --> END
    plan_infra --> END
    click check_app callback "#plan-infra"
    click check_infra callback "#check-infra"
    click plan_infra callback "#check-app"
```

## Inputs

| name                      | type        | description                                                   | default                                                                                                                                                                                                                                                                                                 |
|---------------------------|-------------|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `check-infra`             | `boolean`   | Check and plan the infrastructure                             | `true`                                                                                                                                                                                                                                                                                                  |
| `check-app`               | `boolean`   | Check the application code                                    | `true`                                                                                                                                                                                                                                                                                                  |
| `rust-version`            | `string`    | The Rust version to use.                                      | `${{ vars.RUST_VERSION }}`                                                                                                                                                                                                                                                                              |
| `rust-formatting-version` | `string`    | The Rust version to use to check formatting.                  | `nightly`                                                                                                                                                                                                                                                                                               |
| `rust-protoc`             | `boolean`   | Install `protoc` before running the rust tests.               | `true`                                                                                                                                                                                                                                                                                                  |
| `rust-sccache`            | `boolean`   | Install `sccache` before running the rust tests.              | `true`                                                                                                                                                                                                                                                                                                  |
| `version`                 | `string`    | The version to use in the Terraform `iamge_version` variable. | `latest`                                                                                                                                                                                                                                                                                                |
| `infra-stages`            | json string | The environments to check with Terraform `plan`.              | <pre>[<br>&emsp;{<br>&emsp;&emsp;name: "staging",<br>&emsp;&emsp;url: "https://staging.${{ vars.SUBDOMAIN_NAME }}.walletconnect.com/health"<br>&emsp;},<br>&emsp;{<br>&emsp;&emsp;name: "prod",<br>&emsp;&emsp;url: "https://${{ vars.SUBDOMAIN_NAME }}.walletconnect.com/health"<br>&emsp;}<br>]</pre> |

## Outputs

--

## Permissions

| Permission | Level   |
|------------|---------|
| `contents` | `read`  |
| `id-token` | `write` |

## Repository Variables

- `RUST_VERSION` (only if `inputs.rust-version` is not set)
- `SUBDOMAIN_NAME` (only if `inputs.infra-stages` is not overridden)

- _`AWS_REGION`_
- _`AWS_ROLE_MONITORING`_
- _`GRAFANA_WORKSPACE_NAME`_
- _`OFAC_BLOCKED_COUNTRIES`_
- _`RUN_GROUP`_
- _`TF_DIRECTORY`_

## Repository Secrets

- _`GITHUB_TOKEN`_
- _`TF_API_TOKEN`_

## Dependencies

- [ci-check-app.yml](#app---check)
- [ci-check-infra.yml](#infra---check)
- [ci-plan-infra.yml](#infra---plan)

## Used By

--
