![Netlify Build plugin Angular Serverless – Run Angular Universal seamlessly on Netlify](netlify-plugin-angular.png)

# Angular Universal Plugin

This build plugin is a utility for supporting Angular Universal on Netlify.

## Table of Contents

- [Installation and Configuration](#installation-and-configuration)
- [CLI Usage](#cli-usage)
- [Caveats](#caveats)

## Installation and Configuration

The schematic commands will create a `netlify.toml` in the root of your project, if it doesn't already exist. Your file should include the correct build command, publish directory, and plugins section below. Note: the build command requires you to include your custom project name (as indicated in your angular.json) where designated below:

```toml
[build]
  command = "ng build --configuration production && ng run {projectName}:serverless:production"
  publish = "dist/netlify-serverless/browser"

[[plugins]]
  package = "@netlify/plugin-angular-serverless"
```

## Installation and Configuration

### Manual Installation

Create a `netlify.toml` in the root of your project. Your file should include the plugins section below:

```toml
[build]
  command = "ng build --configuration production && ng run {projectName}:serverless:production"
  publish = "dist/netlify-serverless/browser"

[[plugins]]
  package = "@netlify/plugin-angular-serverless"
```

If you'd like to install this plugin at a fixed version, install it via your package manager:

```bash
# yarn add @netlify/plugin-angular-universal
npm install --save @netlify/plugin-angular-universal
```

Read more about [file-based plugin installation](https://docs.netlify.com/configure-builds/build-plugins/#file-based-installation)
in our docs.

## CLI Usage

If you'd like to build and deploy your project using the
[Netlify CLI](https://docs.netlify.com/cli/get-started/), we recommend this
workflow to manage git tracking plugin-generated files:

1. Make sure all your project's files are committed before running a build with
   the CLI
2. Run any number of builds and deploys freely (i.e. `netlify build`,
   `netlify deploy --build`, `netlify deploy --prod`)
3. Run `git stash --include-unstaged` to easily ignore plugin-generated files

It's important to note that the CLI may mix your project's source code and
plugin-generated files; this is why we recommend committing all project source
files before running CLI builds.

## Caveats

This plugin is currently in beta.

Right now:
- it does not include out of the box monorepo support
- it does not support Angular Universal prerendering