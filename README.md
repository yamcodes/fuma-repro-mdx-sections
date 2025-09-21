# `fuma-repro-mdx-sections`

Reproduction for https://github.com/fuma-nama/fumadocs/issues/2386

## How this repo was created

1. Create a Fumadox project with the following settings:

> [!NOTE] 
> I used pnpm to create the project, but you can use npm yarn.

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

2. Run the development server, e.g. via `pnpm run dev`.

3. Create the following files in the `content/docs` directory: `ex1.mdx`, `ex2.md`.

4. Save the following content in `ex1.mdx`:

```mdx
---
title: Example 1
---

<section id="included">
This is included from mdx.
</section>

This is not included.
```

5. Save the following content in `ex2.md`:

```md
# Example 2

<section id="included">
This is included from md.
</section>

This is not included.
```

6. Append the following content to `index.mdx` (also in `content/docs`):

```mdx
<include>ex1.mdx#included</include>
```

Observe that the included content ("included from mdx") is rendered ✅.

7. Append the following content to `index.mdx` (also in `content/docs`):

```mdx
<include>ex2.md#included</include>
```

Observe that the included content ("included from md") is NOT rendered ❌, and the following build error is displayed:

```
## Error Type
Build Error

## Error Message
Error evaluating Node.js code

## Build Output
./content/docs/index.mdx
Error evaluating Node.js code
Error: index.mdx:Error: Cannot find section included in /Users/yamcodes/code/fuma-repro-mdx-sections/content/docs/ex2.md, make sure you have encapsulated the section in a <section id="included"> tag.
    [at embedContent (file:///Users/yamcodes/code/fuma-repro-mdx-sections/node_modules/.pnpm/fumadocs-mdx@11.10.1_fumadocs-core@15.7.13_@types+react@19.1.13_next@15.5.3_react-dom@1_6e988e38be0df07745612a12063e9754/node_modules/fumadocs-mdx/dist/chunk-SVTXMVLQ.js:85:15)]
    [at async update (file:///Users/yamcodes/code/fuma-repro-mdx-sections/node_modules/.pnpm/fumadocs-mdx@11.10.1_fumadocs-core@15.7.13_@types+react@19.1.13_next@15.5.3_react-dom@1_6e988e38be0df07745612a12063e9754/node_modules/fumadocs-mdx/dist/chunk-SVTXMVLQ.js:125:5)]
    [at async (file:///Users/yamcodes/code/fuma-repro-mdx-sections/node_modules/.pnpm/fumadocs-mdx@11.10.1_fumadocs-core@15.7.13_@types+react@19.1.13_next@15.5.3_react-dom@1_6e988e38be0df07745612a12063e9754/node_modules/fumadocs-mdx/dist/chunk-SVTXMVLQ.js:128:5)]

Next.js version: 15.5.3 (Turbopack)
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

2. Open the project via:

```sh
cd .
pnpm run dev
```

3. Run the development server

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
