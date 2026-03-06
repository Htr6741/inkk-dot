# inkk dot

Personal blog — book reviews, essays, photos, and notes by Hunter.

Built with [Astro](https://astro.build). Hosted on [Cloudflare Workers](https://developers.cloudflare.com/workers/).

**Live:** https://inkk-dot.hunter-077.workers.dev

---

## Writing a New Post

Create a `.md` file in `src/content/blog/`:

```markdown
---
title: "Your Post Title"
date: 2026-03-06
description: "A short summary for previews."
category: book-review
tags: ["fiction", "favourite"]
---

Your content here. Regular **markdown** works.
```

### Frontmatter fields

| Field         | Required | Values                                       |
|---------------|----------|----------------------------------------------|
| `title`       | yes      | Post title                                   |
| `date`        | yes      | `YYYY-MM-DD`                                 |
| `description` | yes      | Short summary                                |
| `category`    | yes      | `book-review`, `essay`, `tech`, or `photo`   |
| `tags`        | no       | Array of strings, e.g. `["fiction", "2026"]`  |
| `image`       | no       | Path to image, e.g. `"/photos/my-photo.jpg"` |

### Photo posts

1. Put images in `public/photos/`
2. Create a post with `category: photo` and `image: "/photos/your-image.jpg"`

### File naming

Use kebab-case for filenames — the filename becomes the URL slug:
- `the-master-and-margarita.md` → `/blog/the-master-and-margarita`

---

## Publishing

```bash
cd ~/inkk-dot
git add .
git commit -m "post: your post title"
git push
CLOUDFLARE_API_TOKEN="<your-token>" npx wrangler deploy --name inkk-dot
```

---

## Local Development

```bash
npm install          # install dependencies
npm run dev          # dev server at localhost:4321
npm run build        # production build to ./dist/
```

---

## Stack

- **Framework:** Astro 5
- **Fonts:** JetBrains Mono, Lora, LXGW WenKai (Chinese)
- **Hosting:** Cloudflare Workers
- **Repo:** GitHub
