# microdocs

> build a minimalist site for your documentation

This module generates a documentation site from two simple components: 

1. A collection of markdown documents
2. A page layout with a navigation liks

This module is intentionally simpler, that might be good, because it's easier to reason about, and it'll probably be most useful if your documentation already consists entirely of markdown files.

Sites are built using a command-line tool from [jus](http:// jus.js.org). you can specify a project logo, custom css, and other basic formatting.

## Getting Started
Clone this repos then install jest and run it to see microdocs :

```
npm i -g jus && jus serve
```

## Deployment to GitHub Pages

Add the following to your package.json:

```json
{
  "scripts": {
    "start": "jus serve",
    "deploy": "npm run build && npm run commit && npm run push && npm run open",
    "build": "jus build . dist",
    "commit": "git add dist && git commit -m 'update dist'",
    "push": "git subtree push --prefix dist origin gh-pages",
    "open": "open http://yoursite.com"
  }
}
```

Now whenever you want to publish to GitHub Pages, run:

```sh
npm run deploy
```

Note: GitHub's [User Pages](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages) (like `yourname.github.io`) are built from the `master` branch,
whereas [Project Pages](https://help.github.com/articles/user-organization-and-project-pages/#project-pages) (like `yourname.github.io/project`) are built from the `gh-pages` branch.
Be aware of this when setting up your npm scripts.

Note: GitHub's CDN can take a minute to update, so you might have to refresh a few times when visiting.

## Deployment to Surge

[surge.sh](https://surge.sh/) is an awesome new platform for publishing static websites.

Install the Surge CLI:

```sh
 npm i -g surge
 ```

Add the following to your package.json:

```json
{
  "scripts": {
    "start": "jus serve",
    "deploy": "npm run build && npm run build && npm run open",
    "build": "jus build . dist",
    "push": "surge dist YOUR-URL",
    "open": "open YOUR-URL"
  }
}
```

Now whenever you want to publish to Surge, run:

```sh
npm run deploy
```