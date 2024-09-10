# React Standalone Component Boilerplate

A boilerplate for developing standalone React components with Storybook and publishing them to npm. This setup supports TypeScript and Material-UI (v5 and v6) out of the box.

## Features

- **ESM and CJS builds**: Export in modern JavaScript module formats (`esm`, `cjs`), with optional `.d.ts` TypeScript definitions.
- **Storybook**: For isolated component development and testing.
- **Rollup**: Used for building components.
- **TypeScript support**: Pre-configured for seamless integration.

<!-- FIXME: add one more feature  - MUI5/6 compatible, and some where section for MUI specific steps -->

## Getting Started

### Prerequisites

Ensure you have the following tools installed:

- Node.js >= 18.x
- Yarn >= 1.x

### Installation


<!-- FIXME: this is template repo, fix installations instructions according to -->
Clone the repository and install dependencies: 

```bash
git clone git@github.com:kantorv/react-external-lib.git
cd react-external-lib-boilerplate
yarn install
```

### Available Scripts

Here are the main scripts you can use:

#### `yarn storybook`

Launches Storybook for developing and testing your components in isolation.

> **Note:** To deploy Storybook to GitHub Pages, make sure your repository settings are properly configured:
>
> 1. Go to `Settings` -> `Actions` -> `General` -> `Workflow permissions`, and enable `Read and write permissions`.
> 2. Go to `Settings` -> `Pages` -> `Build and deployment`, and set the `Source` to `GitHub Actions`.

#### `yarn test`

Runs the test suite using `react-scripts`.

#### `yarn build`

Builds the component library using Rollup, outputting both `esm` and `cjs` formats.

#### `yarn release`

Prepares and publishes a new version to npm. 

> **Note:** Ensure that you have configured your `NPM_PUBLISH_TOKEN` in your repository secrets before running this command.

### Configuration

#### TypeScript (`tsconfig.json`)

This project includes a customized `tsconfig.json` file optimized for generating `.d.ts` declaration files.

### Publishing to npm

To publish your component library, follow these steps:

1. **Generate an npm token**:
    - Go to [npmjs.com](https://npmjs.com), log in, and navigate to `Access Tokens`.
    - Create a new token of type `Classic`, and choose the `Automation` option.

2. **Test locally**:
    ```bash
    npm config set //registry.npmjs.org/:_authToken $NPM_PUBLISH_TOKEN
    npm publish
    ```

3. **GitHub Actions setup**:
    Add the `NPM_PUBLISH_TOKEN` as a secret in your GitHub repository if you want to automate releases via GitHub Actions.

## Known Issues

- Release-it
    - **NPM Classic Token bypasses 2FA**: The token used for automated publishing bypasses two-factor authentication.
    - **GitHub Actions fail on protected branches**: If `git.commit === true` in the `release-it` configuration, the `release.yml` action will fail on protected branches. 
    To resolve this, disable branch protection for the `default` branch. TODO: refactor flow without to `default`  branch

## Inspiration

This project was inspired by:

- [TypeScript React Package Starter](https://github.com/TimMikeladze/typescript-react-package-starter)

## References
- [TypeScript library tips: Rollup your types!](https://medium.com/@martin_hotell/typescript-library-tips-rollup-your-types-995153cc81c7)
- [Creating a React Component Library with TypeScript, Storybook & Rollup](https://blog.cristiana.tech/creating-a-react-component-library-with-typescript-storybook-and-rollup)
- [How to Create a React Multi-package UI Library](https://medium.com/@maayan_37411/how-to-create-a-react-multi-package-ui-library-2ba6ae0909b6)

## Credits
- [Create React App](https://github.com/facebook/create-react-app)
- [StoryBook](https://storybook.js.org/)development and testing
- [Rollup](https://rollupjs.org/) 