# Installation

## Installation via the CLI

The easiest way to install Statamic together with Peak is to use the [official CLI](https://github.com/statamic/cli). Install the CLI by running `composer global require statamic/cli` and for each project just run `statamic new my-site studio1902/statamic-peak`.

> The Peak install process uses Laravel Prompts. Some prompts are *not properly support on Windows without WSL* and will be skipped. This means during the setup process Peak cannot set a timezone for your app. The [Commands Addon](/getting-started/commands.html) won't offer you to pick an icon when adding Page Builder Blocks or Bard Sets. Instead it will pick the first available icon. You can always change these manually in the Statamic Blueprint Builder.

## Install into an existing Statamic v5 project

If you already have an existing, clean, Statamic installation you can run the following command: `php please starter-kit:install studio1902/statamic-peak`.

## Installation options
Make sure you [update the Statamic CLI](https://github.com/statamic/cli#updating-the-cli-tool) to v2.5 or newer to use this functionality. When Statamic installs the Starter Kit, Peak will offer a few options that make configuring your site easier. These include:

1. Installing the paid [Peak Commands addon](/getting-started/commands.html).
2. Copying over the `.env.example` (recommended Peak config) to your `.env`.
3. Setting an app name.
4. Setting your license key.
5. Setting the default site locale.
6. Enabling/disabling the debugbar.
7. Using Imagick instead of GD as an image processor.
8. Configuring a local mailer.
9. Excluding `public/build` from git.
10. Excluding `users` from git.
11. Excluding `storage/form` from git.
12. Adding a GitHub workflow that does [PR's with updates](/getting-started/installation.html#github-pr-s-with-updates).
13. Running `npm i`.
14. Installing Browsershot, Image and Puppeteer for [generating social images](/features/social-images-generation.html).
15. Install missing Laravel translation files using `laravel-lang/common`.
16. Starring the Peak repo.
17. Standing up against fascism.

## Compile the frontend assets

The starter kit comes bundles with compiled assets. Run `npm i && npm run dev` to compile your frontend assets. Use `npm run watch` to watch and compile whenever you made any changes.

Since we use the Tailwind CSS JIT compiler, as soon as you make changes you need to compile them yourself. Compilation is configured in `vite.config.js`. Make sure you add your hostname to your `.env` file (`APP_URL`) as it's being used for the Vite dev server.

```bash
npm i && npm run watch
```

To compile for production run this (on your server). Since Peak uses the Tailwind CSS JIT compiler this won't purge anything, but it will minify your assets:

```bash
npm run build
```
## README and deployment

Peak ships with a README file you can use. It features:

* Installation instructions
* A place to dump your non sensitive `.env` variables
* An example `.env.` for production.
* Nginx configuration for static resource caching.
* [Deploy scripts](/other/deployment-script.html) for Ploi and Forge.

## GitHub PR's with updates

During the Peak installation process you get offered an option to generate a GitHub workflow file that automatically creates PR's with composer updates for you. You can configure the workflow to run:

* Every week
* Every month
* Every three months
* Never, you trigger this manually on github.com

Note that in order for this to work, you have to have configure your GitHub workflow permissions to read and write and allow GitHub actions to create and approve pull requests.
