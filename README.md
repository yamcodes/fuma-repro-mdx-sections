# `fuma-repro-mdx-sections`

Reproduction for (insert link to issue here)

## How this repo was created

1. Create a Fumadox project with the following settings:

```sh
~/code/fuma-repro-mdx-sections 
❯ pnpm create fumadocs-app .
.../19962af411f-3268                     |   +7 +
.../19962af411f-3268                     | Progress: resolved 7, reused 2, downloaded 5, added 7, done
┌  Create Fumadocs App
│
◇  Choose a template
│  Next.js: Fumadocs MDX
│
◇  Use `/src` directory?
│  No
│
◇  Configure linter?
│  Disabled
│
◇  Do you want to install packages automatically? (detected as pnpm)
│  Yes
│
◇  Project Generated
│
└  Done


Open the project
cd .

Run Development Server
npm run dev | pnpm run dev | yarn dev

You can now open the project and start writing documents
```

---

This is a Next.js application generated with
[Create Fumadocs](https://github.com/fuma-nama/fumadocs).

Run development server:

```bash
npm run dev
# or
pnpm dev
# or
yarn dev
```

Open http://localhost:3000 with your browser to see the result.

## Explore

In the project, you can see:

- `lib/source.ts`: Code for content source adapter, [`loader()`](https://fumadocs.dev/docs/headless/source-api) provides the interface to access your content.
- `lib/layout.shared.tsx`: Shared options for layouts, optional but preferred to keep.

| Route                     | Description                                            |
| ------------------------- | ------------------------------------------------------ |
| `app/(home)`              | The route group for your landing page and other pages. |
| `app/docs`                | The documentation layout and pages.                    |
| `app/api/search/route.ts` | The Route Handler for search.                          |

### Fumadocs MDX

A `source.config.ts` config file has been included, you can customise different options like frontmatter schema.

Read the [Introduction](https://fumadocs.dev/docs/mdx) for further details.

## Learn More

To learn more about Next.js and Fumadocs, take a look at the following
resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js
  features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.
- [Fumadocs](https://fumadocs.vercel.app) - learn about Fumadocs
