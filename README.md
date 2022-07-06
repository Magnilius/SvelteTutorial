## Desc

This is my first try on Svelte JS with SvelteKit.

If you clone the app, you will be able to use only when you register yourself to moviedb, and then you have to make your own API key. The API key is used in routes/index.svelte, routes/movie/[id].svelte, routes/search/[id].svelte.

This project was made as a tutorial, and I was watching a youtube video about it. Thanks for that Dev Ed!

# create-svelte

Everything you need to build a Svelte project, powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npm init svelte

# create a new project in my-app
npm init svelte my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://kit.svelte.dev/docs/adapters) for your target environment.
