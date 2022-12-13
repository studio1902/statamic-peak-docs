# Contributing
Contributions and discussions are always welcome, no matter how large or small.

## Test the kit
If you want to install and test your locally exported kit, make sure you add the repo's local path to your global Composer `config.json` file as a repository:

```json
{
    "repositories": [
        {
            "type": "path",
            "url": "/Users/robdekort/statamic-peak"
        }
    ]
}
```

You can then run `statamic new site studio1902/statamic-peak --local` to run the Statamic installer using your own locally exported starter kit.

## Docs
The documentation run on https://vuepress.vuejs.org. To locally install this run the following:

1. `npm i`
2. `npm run docs:dev`
3. Visit http://localhost:8080.

Commits to these docs are automatically deployed to production on https://peak.1902.studio using [Netlify](https://netlify.com).

## Attribution
These docs are initially setup using VuePress 1 by [Robert Guss](https://github.com/robertguss/). Thank you so much! Today we run VuePress 2.
