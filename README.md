## Building a Marketplace

Here's a great frustrating project to get on with!

#### Frontend

`Next.JS`

#### Backend

`Medusa.JS` `Node.JS` `PostgreSQL` `Redis`

## Medusa.JS

Begin by reading [the docs](https://docs.medusajs.com/)

- [Start up a backend with Railway](https://docs.medusajs.com/deployments/server/deploying-on-railway)
- [Start up a frontend and connect it to your backend](https://docs.medusajs.com/starters/nextjs-medusa-starter) grab your `DB_URL` fill that in on the backend
- test and see you can speak to your backend locally `curl localhost:9000/store/products`
- Check the deployed DB on [Postman](https://web.postman.co/workspace/) `GET` `https://backend-production-......railway.app/store/products`
- [Deploy your frontend on Vercel](https://docs.medusajs.com/deployments/storefront/deploying-next-on-vercel)

  - only works with `NEXT_PUBLIC_MEDUSA_BACKEND_URL` (`https://backend-.......up.railway.app`) `NEXT_PUBLIC_BASE_URL` `REVALIDATE_SECRET` don't add any others

### Extending the Marketplace

- add in search
- test search

### extended into a marketplace

- Every time a user is created, a new store associated with that user is created.
- When the user retrieves the store’s details, their store’s details will be retrieved.
- Every time a product is created, it is associated with the store of the logged-in user.
- The user will only be able to retrieve products from their store.

### [extending-medusa-usecase-marketplace](https://medusajs.com/blog/extending-medusa-usecase-marketplace/)

[tutorial repo](https://github.com/shahednasser/medusa-1.8-marketplace-tutorial?tab=readme-ov-file)

[Make sure you are on version 1.8](https://docs.medusajs.com/upgrade-guides/medusa-core/1-8-0)

- Every time a user is created, a new store associated with that user is created.
- When the user retrieves the store’s details, their store’s details will be retrieved.
- Every time a product is created, it is associated with the store of the logged-in user.
- The user will only be able to retrieve products from their store.

---

- Users now have a `store_id` assigned on creation
- `store_id` is a column for every product

What’s Next
In this tutorial, you learned how to implement the foundation of a marketplace: having multiple stores, different users within those stores, and associating products with a store.
A marketplace has a variety of other features, each depending on your use case. Some of them are:
Create order-store relation: This requires a similar implementation as what you’ve done in this tutorial with products and users. You need to extend the Copy to clipboard
Order
entity to include a relation to the store. You can learn more about extending entities in the documentation.
List orders by stores: This requires a similar implementation as what you’ve done in this tutorial with products. You need to extend the Copy to clipboard
OrderService
to override the methods used to retrieve orders. You can learn more about extending services in the documentation.
Associate an order to a store: This requires listening to the Copy to clipboard
order.created
event in a subscriber. The implementation can include creating child orders of an order if in your use case you support have products from multiple stores in one product. In this case, you’d also need to extend the order entity to create a parent-child relation. You can learn more about subscribers in the documentation.
Implement teams within a store: You can implement a team within a store by extending the Copy to clipboard
Invite
entity to associate it with a store ID, then associate the user created from the invite with that store ID.

<p align="center">
  <a href="https://www.medusajs.com">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://user-images.githubusercontent.com/59018053/229103275-b5e482bb-4601-46e6-8142-244f531cebdb.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://user-images.githubusercontent.com/59018053/229103726-e5b529a3-9b3f-4970-8a1f-c6af37f087bf.svg">
    <img alt="Medusa logo" src="https://user-images.githubusercontent.com/59018053/229103726-e5b529a3-9b3f-4970-8a1f-c6af37f087bf.svg">
    </picture>
  </a>
</p>

<h1 align="center">
  Medusa Next.js Starter Template
</h1>

<p align="center">
Combine Medusa's modules for your commerce backend with the newest Next.js 14 features for a performant storefront.</p>

<p align="center">
  <a href="https://github.com/medusajs/medusa/blob/master/CONTRIBUTING.md">
    <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat" alt="PRs welcome!" />
  </a>
  <a href="https://discord.gg/xpCwq3Kfn8">
    <img src="https://img.shields.io/badge/chat-on%20discord-7289DA.svg" alt="Discord Chat" />
  </a>
  <a href="https://twitter.com/intent/follow?screen_name=medusajs">
    <img src="https://img.shields.io/twitter/follow/medusajs.svg?label=Follow%20@medusajs" alt="Follow @medusajs" />
  </a>
</p>

### Prerequisites

To use the [Next.js Starter Template](https://medusajs.com/nextjs-commerce/), you should have a Medusa server running locally on port 9000.
For a quick setup, run:

```shell
npx create-medusa-app@latest
```

Check out [create-medusa-app docs](https://docs.medusajs.com/create-medusa-app) for more details and troubleshooting.

# Overview

The Medusa Next.js Starter is built with:

- [Next.js](https://nextjs.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Typescript](https://www.typescriptlang.org/)
- [Medusa](https://medusajs.com/)

Features include:

- Full ecommerce support:
  - Product Detail Page
  - Product Overview Page
  - Search with Algolia
  - Product Collections
  - Cart
  - Checkout with PayPal and Stripe
  - User Accounts
  - Order Details
- Next.js 14
- Full App Router support with [Dynamic Routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes) and [Route Groups](https://nextjs.org/docs/app/building-your-application/routing/route-groups)
- [Product Module](https://docs.medusajs.com/modules/products/serverless-module) support (beta)

# Quickstart

### Setting up the environment variabless

Navigate into your projects directory and get your environment variables ready:

```shell
cd nextjs-starter-medusa/
mv .env.template .env.local
```

### Install dependenciess

Use Yarn to install all dependencies.

```shell
yarn
```

### Start developing

You are now ready to start up your project.

```shell
yarn dev
```

### Open the code and start customizing

Your site is now running at http://localhost:8000!

# Payment integrations

By default this starter supports the following payment integrations

- [Stripe](https://stripe.com/)
- [Paypal](https://www.paypal.com/)

To enable the integrations you need to add the following to your `.env.local` file:

```shell
NEXT_PUBLIC_STRIPE_KEY=<your-stripe-public-key>
NEXT_PUBLIC_PAYPAL_CLIENT_ID=<your-paypal-client-id>
```

You will also need to setup the integrations in your Medusa server. See the [Medusa documentation](https://docs.medusajs.com) for more information on how to configure [Stripe](https://docs.medusajs.com/add-plugins/stripe) and [PayPal](https://docs.medusajs.com/add-plugins/paypal) in your Medusa project.

# Search integration

This starter is configured to support using the `medusa-search-meilisearch` plugin out of the box. To enable search you will need to enable the feature flag in `./store.config.json`, which you do by changing the config to this:

```javascript
{
  "features": {
    // other features...
    "search": true
  }
}
```

Before you can search you will need to install the plugin in your Medusa server, for a written guide on how to do this – [see our documentation](https://docs.medusajs.com/add-plugins/meilisearch).

The search components in this starter are developed with Algolia's `react-instant-search-hooks-web` library which should make it possible for you to seemlesly change your search provider to Algolia instead of MeiliSearch.

To do this you will need to add `algoliasearch` to the project, by running

```shell
yarn add algoliasearch
```

After this you will need to switch the current MeiliSearch `SearchClient` out with a Alogolia client. To do this update `@lib/search-client`.

```ts
import algoliasearch from "algoliasearch/lite"

const appId = process.env.NEXT_PUBLIC_SEARCH_APP_ID || "test_app_id" // You should add this to your environment variables

const apiKey = process.env.NEXT_PUBLIC_SEARCH_API_KEY || "test_key"

export const searchClient = algoliasearch(appId, apiKey)

export const SEARCH_INDEX_NAME =
  process.env.NEXT_PUBLIC_INDEX_NAME || "products"
```

Then, in `src/app/(main)/search/actions.ts`, remove the MeiliSearch code (line 10-16) and uncomment the Algolia code.

```ts
"use server"

import { searchClient, SEARCH_INDEX_NAME } from "@lib/search-client"

/**
 * Uses MeiliSearch or Algolia to search for a query
 * @param {string} query - search query
 */
export async function search(query: string) {
  const index = searchClient.initIndex(SEARCH_INDEX_NAME)
  const { hits } = await index.search(query)

  return hits
}
```

After this you will need to set up Algolia with your Medusa server, and then you should be good to go. For a more thorough walkthrough of using Algolia with Medusa – [see our documentation](https://docs.medusajs.com/add-plugins/algolia), and the [documentation for using `react-instantsearch-hooks-web`](https://www.algolia.com/doc/guides/building-search-ui/getting-started/react-hooks/).

# Serverless Modules

> Serverless Modules are currently in beta. You can learn more about them [here](https://docs.medusajs.com/experimental). In addition, the Serverless Modules in the Next.js storefront can't be used without the Medusa backend running at the moment.

This starter has full support for our new experimental [Product Module](https://docs.medusajs.com/experimental/product/overview) and [Pricing Module](https://docs.medusajs.com/experimental/pricing/overview) for retrieving and manipulating product and pricing data directly from a serverless function. This keeps your product logic close to the frontend, making it easy to customize or extend Medusa's core functionality from within your Next.js project.

By default, this starter uses the standard Medusa API for product and collection retrieval.

To enable the new modules on your server, refer to their [docs](https://docs.medusajs.com/experimental).

Then, make sure to set the following environment variables in your Next.js storefront project:

> WARNING: This is a one way process. Once you opt in to these features and update your database, there's no way back. Proceed with caution.

- `POSTGRES_URL`: the URL of your PostgreSQL databsae.
- `NEXT_PUBLIC_BASE_URL`: the URL of your storefront's base URL. If you're running it locally, it should be http://localhost:8000.

After that, add the following environment variable to **both your Next.js storefront and Medusa backend** to enable the feature flag:

- `MEDUSA_FF_MEDUSA_V2=true`

Finally, run migrations in your Medusa backend to prepare your database for the new modules.

```shell
npx medusa migrations run
```

Make sure the Medusa backend is running, then start (or restart) your Next.js storefront.

Done! All product and collection data should now be coming from the module. The Product Module routes are all in `src/app/api` for you to edit and play around with.

> Deploying to Vercel? If you're not planning on using the serverless modules, you might encounter errors when deploying to Vercel. You can safely delete or exclude the `src/app/api` folder before deploying. The API routes are only used by the serverless modules.

# Resources

## Learn more about Medusa

- [Website](https://www.medusajs.com/)
- [GitHub](https://github.com/medusajs)
- [Documentation](https://docs.medusajs.com/)

## Learn more about Next.js

- [Website](https://nextjs.org/)
- [GitHub](https://github.com/vercel/next.js)
- [Documentation](https://nextjs.org/docs)
