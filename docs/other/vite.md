# Vite

Peak ships with a simple Vite config file to compile your assets and hot serve your website. When you want to use self-signed certificates and Browsersync to test your local website on local mobile devices, you can expand the config.

## Vite advanced config

Install Browser Sync:
```bash
npm i vite-plugin-browser-sync
```

Add a `sync` option to your scripts in `package.json`:
```js
"scripts": {
    "dev": "vite",
    "watch": "vite",
    "sync": "VITE_BROWSERSYNC=true vite",
    "build": "vite build",
    "production": "vite build"
},
```

Update your `vite.config.js`:
```js
import laravel from 'laravel-vite-plugin'
import { defineConfig, loadEnv } from 'vite'
import { networkInterfaces } from 'os'
import VitePluginBrowserSync from 'vite-plugin-browser-sync'

/** @type {import('vite').UserConfig} */
export default defineConfig(({ mode }) => {
    const env = loadEnv(mode, process.cwd(), '')
    const ip = Object.values(networkInterfaces()).flat().find((i) => i.family === 'IPv4' && !i.internal)?.address
    const isSecuredSite = env.APP_URL.startsWith('https://')
    const url = env.APP_URL
    const host = url.replace(/^https?:\/\//, '')
    const useBrowserSync = env.VITE_BROWSERSYNC && ip

    if (useBrowserSync && isSecuredSite) {
        console.log('\x1b[31m%s\x1b[0m', 'Sorry, we didn\'t manage to get BrowserSync working with secured sites.');
        console.log('\x1b[31m%s\x1b[0m', 'If you can provide a solution, please enlighten us (https://github.com/studio1902/statamic-peak/pulls).');
        process.exit(1)
    }

    return {
        plugins: [
            laravel({
                refresh: true,
                valetTls: isSecuredSite ? host : false,
                input: [
                    'resources/css/site.css',
                    'resources/js/site.js',
                ]
            }),
            (() => {
                return useBrowserSync ? VitePluginBrowserSync({
                    bs: {
                        proxy: url,
                        notify: false,
                        open: 'external',
                    },
                }) : null;
            })()
        ],
        server: {
            host: useBrowserSync ? ip : host,
            open: useBrowserSync ? false : url,
        }
    }
});
```
