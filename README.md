# A Blog example using Astro and DatoCMS

This example showcases an Astro Blog using [DatoCMS](https://www.datocms.com/) as the data source.
The purpose of this repo is to have a quick start reference that can be set up with the "one-click" button below.

## Demo

Have a look at the end result live:

### [https://blog-astro-no-clientside-js.vercel.app/](https://blog-astro-no-clientside-js.vercel.app/)

## How to use

### Quick start

1. [Create an account on DatoCMS](https://datocms.com).

2. Make sure that you have set up the [Github integration on Vercel](https://vercel.com/docs/git/vercel-for-github).

3. Let DatoCMS set everything up for you clicking this button:

[![Deploy with DatoCMS](https://dashboard.datocms.com/deploy/button.svg)](https://dashboard.datocms.com/projects/clone?repo=/marcelofinamorvieira/blog-astro-no-clientside-js)

### Local setup

Once the setup of the project and repo is done, clone the repo locally.

#### Set up environment variables

In your DatoCMS' project, go to the **Settings** menu at the top and click **API tokens**.

Then click **Read-only API token** and copy the token.

Next, create the `.env` with your API token (which will be ignored by Git):

```bash
echo ASTRO_EXAMPLE_CMS_DATOCMS_API_TOKEN=<YOUR_API_TOKEN> >> .env
```

#### Run your project locally

```bash
npm install
npm run dev
```

Your blog should be up and running on [http://localhost:3000](http://localhost:3000)!

## `client:visible` directive

Astro is ["Zero JS, by default: No JavaScript runtime overhead to slow you down"](https://docs.astro.build/en/getting-started/). That means that by default Astro generates static files server-side and no JS is sent to the client, unless strictly needed.

When using the `<Image />` component, or any other component that requires some client-side orchestration, you must instruct Astro to send the component bundle to the client, so that the interactive features can be made available to the user. Astro uses [_directives_](https://docs.astro.build/en/reference/directives-reference/#client-directives): `client:visible` loads and hydrates the component once the component has entered the user’s viewport.

In this demo, we use the `client:visible` directive to enable the lazy load of images, that are actually loaded only when they enter the viewport.
