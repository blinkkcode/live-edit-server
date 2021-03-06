# editor.dev Connector

Provides an API server for the editor to connect to and request project files and perform operations.

See the [docs][docs] or [typescript docs][tsdocs].

[docs]: https://editor.dev/docs/
[tsdocs]: https://editor.dev/api/connector/

## Usage

To use `editor.dev` with your local project run the following in your project directory (does not need to be added to your node dependencies):

```sh
# Requires Node 14+.
npx @blinkk/editor.dev
```

## Deployment

The editor server is built for production using a Docker image and Google Cloud Run.

Every commit to `main` builds the docker image with a `:main` tag and updates the cloud run image for `api.beta.editor.dev`.
Every tag builds the docker image with a version tag (ex: `v1.0.5`) and the `:latest` tag then updates the cloud run image for `api.editor.dev`.

If there is an issue with the latest release for the prod api you can roll back to an earlier version.

To switch the production deployment run `make deploy-prod tag=<VERSION>` where `<VERSION>` is the
desired version to roll back to. For example: `make deploy-prod tag=v1.0.5`.

## Development

To develop on the editor server for local projects, run the following command:

```sh
# ex: yarn run serve ~/code/project
yarn run serve <project_dir>
```

If you are developing the hosted version of the server (that provides access to github, etc) then run the following command:

```sh
yarn run hosted
```
