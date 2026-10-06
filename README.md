# payz-sdk

The typed TypeScript client for the Payz API. The repository includes generated API operations and schemas, React Query hooks, and a configurable fetch adapter.

## Workspace dependencies

This source package is developed in a pnpm workspace with `payz-core`. Code generation also reads the OpenAPI file from the separate `payz-docs` repository and writes generated schemas into `payz-core`. These repositories remain independent; this repository does not include or publish their source.

## Local development

Use Node.js 22 or newer and pnpm 10. Clone this repository and `payz-core` into `repos/`, then copy the minimal workspace files from this repository:

```sh
mkdir -p repos
git clone https://github.com/payz-world/payz-sdk.git repos/payz-sdk
git clone https://github.com/payz-world/payz-core.git repos/payz-core
cp repos/payz-sdk/development/package.json ./package.json
cp repos/payz-sdk/development/pnpm-workspace.yaml ./pnpm-workspace.yaml
cp repos/payz-sdk/development/tsconfig.base.json ./tsconfig.base.json
pnpm install
pnpm typecheck
```

Typecheck compiles the published SDK source. To regenerate it, also check out `payz-docs` under `repos/payz-docs` so `spec/openapi.yaml` is available, then run:

```sh
pnpm generate
```

Generation updates files in both `repos/payz-sdk` and `repos/payz-core`. Review and commit each repository's changes separately.

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE).
