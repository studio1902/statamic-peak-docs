# Installation

## Installation via the CLI

The easiest way to install Statamic together with Peak is to use the [official CLI](https://github.com/statamic/cli). Install the CLI by running `composer global require statamic/cli` and for each project just run `statamic new my-site studio1902/statamic-peak`.

The Peak install process uses Laravel Prompts. Some prompts are not properly support on Windows without WSL.

## Install into an existing Statamic v3.3+ project

If you already have an existing, clean, Statamic installation you can run the following command: `php please starter-kit:install studio1902/statamic-peak`.

## Installation options
Make sure you [update the Statamic CLI](https://github.com/statamic/cli#updating-the-cli-tool) to v2.5 or newer to use this functionality. When Statamic installs the Starter Kit, Peak will offer a few options that make configuring your site easier. These include:

1. Copy over the `.env.example` (recommended Peak config) to your `.env` whilst maintaining your `APP_KEY` and `APP_URL` and setting a custom `APP_NAME`.
2. Using Imagick instead of GD as an image manipulation driver.
3. Enabling `SAVE_CACHED_IMAGES`.
4. Initialising a Git repo.
5. Adding `/users` to `.gitignore` to avoid GDPR issues.
6. Adding `/storage/forms` to `.gitignore` to avoid GDPR issues.
7. Adding `/public/build` to `.gitignore` for when you compile assets on your server.
8. Running `npm i`.
9. Installing Browsershot and Puppeteer.
10. Starring the Peak repo.

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
