# React Standalone Component Boilerplate

A boilerplate for developing standalone React components with Storybook and publishing them to npm.

## Features

- **Rollup**: Build  `esm` and/or`cjs` formats, with optional `.d.ts`.
- **Release-it**: release-it integration for github releases, and npmjs publishing
- **Storybook**: For component development, testing, and presentation.
- **SDLC**: github actions ( with release-it), gitflow support, usage of PR labels (for setting semver release type) allow to implement different sdlc flows and releases logic.


## Out the box support:
- **TypeScript**: Pre-configured for seamless integration.
- **Material-UI**: Compatible with MUI v5/v6.

## Getting Started


### Prequirements
1. **NPM publish token**

    - Go to [npmjs.com](https://npmjs.com), log in, and navigate to `Access Tokens`.
    - Create a new token of type `Classic`, and choose the `Automation` option.

    - Install token to `~/.npmrc`:
        ```bash
        $ npm config set //registry.npmjs.org/:_authToken $NPM_PUBLISH_TOKEN
        ```

### Installation

To create a new project from this template:

1. Click on the `Use this template` button in GitHub.
2. Clone the newly created repository:
    ```bash
    git clone git@github.com:yourusername/react-external-lib.git my-cistom-lib
    cd my-custom-lib
    yarn install
    yarn storybook
    yarn build
    yarn release # make sure you have a valid NPM_PUBLISH_TOKEN
    
    # ci env simulate
    # yarn release --ci  --increment=minor
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

> **Note:** Ensure that you have configured your `NPM_PUBLISH_TOKEN` in your repository secrets before running this command in github action.

### Configuration

#### TypeScript (`tsconfig.json`)

The provided `tsconfig.json` contains several options related to generated `.d.ts` - required by `rollup-plugin-dts`
- `"declaration": true`
- `"declarationDir": "build/dts"`
- `"emitDeclarationOnly": true`



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
    To resolve this, disable branch protection for the `default` branch. 
     TODO: refactor flow without commiting to `default`  branch

## Inspiration

This project was inspired by:

- [TypeScript React Package Starter](https://github.com/TimMikeladze/typescript-react-package-starter)

## References
- [TypeScript library tips: Rollup your types!](https://medium.com/@martin_hotell/typescript-library-tips-rollup-your-types-995153cc81c7)
- [Creating a React Component Library with TypeScript, Storybook & Rollup](https://blog.cristiana.tech/creating-a-react-component-library-with-typescript-storybook-and-rollup)
- [How to Create a React Multi-package UI Library](https://medium.com/@maayan_37411/how-to-create-a-react-multi-package-ui-library-2ba6ae0909b6)

## Credits
- [Create React App](https://github.com/facebook/create-react-app)
- [StoryBook](https://storybook.js.org/)
- [Rollup](https://rollupjs.org/) 