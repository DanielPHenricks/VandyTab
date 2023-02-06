# Vandy Tab in Svelte

This is a one-tab application in progress. This is a modernized version of the original Vandy Tab application built in Svelte. See instructions below for installation:

# Last updated: 2/6/2023

## How to get started

Install the dependencies...

```bash
cd svelte-app
npm install
```

And start via:

```bash
npm run dev
```

## How to view your code with live reloads

Navigate to [localhost:5173](http://localhost:5173). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

If you're using [Visual Studio Code](https://code.visualstudio.com/) we recommend installing the official extension [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode). If you are using other editors you may need to install a plugin in order to get syntax highlighting and intellisense.

## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

## Deploying the Chrome Extension:

Follow these steps:

1) Build the project into the dist/ folder.
2) Navigate to [chrome://extensions](chrome://extensions)
3) Toggle on dev mode and unpack the app.
4) Reload Chrome and the homepage should be set by default!