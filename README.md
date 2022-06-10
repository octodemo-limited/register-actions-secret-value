# register-actions-secret-value

The workflow [create_or_update_repository_secret](.github/workflows/create_or_update_repository_secret.yml) shows how to provide secret create/update functionality on a repository without directly enabling the users with `admin` access on a repository.

The workflow utilizes a `workflow_dispatch` event, so it can be manually run, or called programmatically. It requires the name of the repository to set or update the secret on, the name of the secret and the secret value.

There is an organization owned GitHub Application that has been installed on the repositories that the workflow can create/update secrets on, and this is ued to obtain a temporary credential as part of the workflow to be able to interact with the secrets on the specified repository. This application only has secret write access on the repositories that we want to enable this workflow on.

The secret value is masked and not exposed in a normal workflow operation, it would potentially be exposed if you enabled debug operation though.
