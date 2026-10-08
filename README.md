# Editing Tracey's website

Hi Tracey! You can change most of your website's words and photos without writing code. The pages are stored as **Markdown files** (filenames ending in `.md`). Hugo turns these files into web pages, and Netlify publishes the finished site.

## Quick start: change your About page

1. Sign in to GitHub and open [the website repository](https://github.com/tra227/traceyahrendt).
2. Select the `production` branch, then open `content/about.md`.
3. Open the file editor. Change a sentence below the second `---` line. Keep the settings at the top intact for your first edit.
4. Review the changes and commit them with a short message such as `Update About page introduction`. A commit saves a version of your changes.
5. If Netlify is connected to this repository's `production` branch, the commit starts a new deployment automatically. Check the site's **Deploys** area in Netlify and wait for a successful deployment.
6. Open the live About page and refresh it to check your changes, including on your phone.

You need permission to edit the repository. If GitHub asks you to create a pull request instead of saving to `production`, submit the request for your site maintainer to review and merge. A pull request proposes changes; merging it saves them to the publishing branch.

## Where to find things

Paths below start at the main repository folder.

| What you want to change | File or folder |
| --- | --- |
| About page text and subtitle | `content/about.md` |
| Contact page title and subtitle | `content/contact.md` |
| Phone, email, location, tagline, and default search description | `hugo.toml`, under `[params]` |
| Services page title and description | `content/services/_index.md` |
| Service category title, description, and cover photo | The category's `_index.md`, such as `content/services/family-lifestyle/_index.md` |
| A service's text, photos, and package details | Its `.md` file inside `content/services/` |
| Family Photography | `content/services/family-lifestyle/family-photography.md` |
| Engagement Photography | `content/services/engagement-photography.md` |
| Blog heading and description | `content/blog/_index.md` |
| Portfolio heading and description | `content/portfolio/_index.md` |
| Service photos | `assets/images/services/` |
| Homepage wording | `themes/flavor/layouts/index.html` — ask your maintainer if you are unsure about editing HTML |
| Contact availability wording and form setup | `themes/flavor/layouts/_default/contact.html` — ask your maintainer for help |

Some service files sit directly in `content/services/`; others sit inside a category folder. Browse the folders to find the service you want. Files named `_index.md` describe a section or category, not an individual service.

The Contact template does not display Markdown paragraphs added to `content/contact.md`. The Blog and Portfolio overview templates also use their settings and child pages rather than displaying paragraphs from their `_index.md` files.

## How a Markdown page works

A page has two parts: **settings at the top** and **page text below**. The settings are called front matter and sit between two `---` lines:

```markdown
---
title: "About Me"
layout: "about"
subtitle: "The person behind the lens"
---

## Hi, I'm Tracey

I'm a photographic artist based in Ft. Lauderdale, Florida.

## My Approach

Every session starts with a conversation about your vision.
```

Change words inside the quotes to edit settings. Keep the setting names, colons, and opening and closing `---` lines. Leave `layout` as it is.

Below the settings, write normal paragraphs with a blank line between them. These common Markdown formats work in page text:

| What you want | What to type |
| --- | --- |
| A section heading | `## Your Session` |
| A smaller heading | `### What to Bring` |
| Bold words | `**Please book ahead**` |
| Italic words | `*An evening by the water*` |
| A link to another page | `[Get in touch](/contact/)` |
| A link to another website | `[Visit example](https://example.com)` |
| A photo | `![Family walking on the beach](/images/services/family-1.jpg)` |

For a bullet list, put each item on its own line and leave a blank line before the list:

```markdown
What to bring:

- Your favorite outfit
- Comfortable shoes
- Any meaningful props
```

The page template already supplies the main title, so use `##` for headings in the page text.

## Edit a photography service

Open the service's Markdown file. Update the paragraphs below the settings, then update any relevant settings:

- `title`: the page and card title.
- `description`: a short description for search engines and page metadata.
- `excerpt`: the short introduction shown on service cards and the service page.
- `starting_price`: an optional starting price. Use a number such as `600`, without a dollar sign. Remove the whole line to stop displaying a starting price.
- `includes`: an optional list of what the session includes.
- `details`: optional facts such as duration, location, and deliverables.
- `weight`: display order; smaller numbers come first.

For example, a service with package details might include this inside its existing settings block:

```yaml
starting_price: 600
includes:
  - "Pre-session consultation"
  - "One-hour session"
  - "20 professionally edited images"
details:
  Duration: "1 hour"
  Location: "Ft. Lauderdale and surrounding areas"
  Deliverables: "20 edited images"
```

Keep the indentation exactly as shown: two spaces before each list item or detail. Use spaces, not tabs. If a setting is already present, edit it rather than adding a second copy.

Leave `service_group` and `icon` unchanged unless your maintainer is helping reorganize services. Changing a filename can change its web address and break existing links.

To add a service, copy a similar service file into the same category folder with a new lowercase, hyphenated filename, such as `beach-family-photography.md`. Update its title, descriptions, photos, and text; keep the matching `service_group`. Check the category page after publishing. New categories and navigation changes are best handled with your maintainer.

## Change photos

1. Choose a photo you have permission to publish. Use a simple lowercase filename with hyphens, such as `family-beach-session.jpg`.
2. Upload it to `assets/images/services/` in GitHub, or copy it there on your computer.
3. In the service file, update `image` and `image_alt`. The path starts with `images/`, not `assets/`.
4. Update the `gallery` list to choose photos and their order. Each `alt` describes the photo for visitors using screen readers.
5. Review the cover crop and gallery on the finished page.

```yaml
image: "images/services/family-beach-session.jpg"
image_alt: "Parents and children walking together on the beach"
gallery:
  - src: "images/services/family-beach-session.jpg"
    alt: "Parents and children walking together on the beach"
  - src: "images/services/family-2.jpg"
    alt: "Black and white portrait of parents and their children"
```

This example belongs inside the existing front matter block. Replace existing `image`, `image_alt`, and `gallery` settings rather than duplicating them. For a new filename, upload the photo before changing a live page to reference it, or commit both changes together.

Hugo automatically makes smaller WebP versions for supported photos. Upload the source photo, not generated files from `public/` or `resources/`.

Some services currently use stock photos marked as session inspiration. When replacing those with your own matching work, remove `stock_preview: true` and set `photo_preview: false`. If the category cover uses that stock photo too, update its `_index.md` separately. More photo options are explained in [docs/images.md](docs/images.md).

## Add a blog post

Create a new file such as `content/blog/family-session-at-the-beach.md` with this structure. Replace the example title, date, description, and text with your own:

```markdown
---
title: "A Family Session at the Beach"
date: 2026-10-07
description: "A relaxed family photography session in Ft. Lauderdale."
draft: false
---

## An Evening Together

Write your story here.

[Plan your own session](/contact/)
```

Use `YYYY-MM-DD` for dates. Future-dated posts are not published by the normal build until their date arrives and another build runs. Set `draft: true` to keep a post off the live site; change it to `false` when ready. Committing a draft still saves its text in the repository, so do not put private information there.

For a post with photos, see the page-bundle example in [docs/images.md](docs/images.md). To add a Portfolio entry, create a Markdown file inside `content/portfolio/` with `title`, `image`, and `image_alt` settings. The Portfolio overview displays each entry's cover photo; gallery photos inside an entry do not automatically appear on that overview.

## Use Git on your computer

Git lets you download the website, track your edits, and send them to GitHub. Have your maintainer help install Git and set up GitHub sign-in first. You need permission to push to this repository. Run these commands in a terminal, one line at a time.

### First time: download the website

Choose a folder on your computer where you want to keep the website, then open a terminal there:

```sh
git clone --branch production https://github.com/tra227/traceyahrendt.git
cd traceyahrendt
git status
```

`git clone` downloads the repository into a new `traceyahrendt` folder. `cd` moves your terminal into that folder. `git status` shows your current branch and any changed files. You should be on `production`, with a clean working tree before making edits. You only need to clone once.

### Each time: get the latest version

Open a terminal in your existing `traceyahrendt` folder. Check for unfinished edits before downloading updates:

```sh
git status
git pull --ff-only origin production
```

Run the pull when you are on `production` and your working tree is clean. It brings in changes made through GitHub or by your maintainer. If you have unfinished changes or Git reports an error, ask your maintainer for help before continuing.

### After editing: save and publish your changes

Save your files in your text editor and preview them if you have Hugo installed. Then check which files changed:

```sh
git status
```

Stage the files you intend to publish. For example, if you edited your About page:

```sh
git add content/about.md
```

For a photo and its service page, stage both together:

```sh
git add assets/images/services/family-beach-session.jpg content/services/family-lifestyle/family-photography.md
```

Use the actual paths of your changed files. `git add` selects changes for the next commit; it does not publish them. Check the list again, then create a commit and push it:

```sh
git status
git commit -m "Update About page introduction"
git push origin production
git status
```

Replace the commit message with a short description of your edits. `git commit` saves a version on your computer. `git push` sends your commits to GitHub and triggers Netlify when automatic deployment is configured. The final status should show a clean working tree. Wait for Netlify's successful deployment before checking the live site.

If Git asks for your name and email when committing, use your own details:

```sh
git config user.name "Tracey Ahrendt"
git config user.email "YOUR_GITHUB_EMAIL"
```

Replace `YOUR_GITHUB_EMAIL` with the email associated with your GitHub account (or its GitHub-provided private email), then retry the commit. These settings apply to this repository.

If a push is rejected because newer changes exist, or Git reports a conflict or sign-in problem, keep your files and ask your maintainer for help. Do not force-push. If you edit a file again after `git add`, run `git add` for that file again before committing so the latest edits are included.

## Preview on your computer (optional)

GitHub's file preview helps check Markdown formatting, but it does not show the complete website design. To preview the actual site locally, have your maintainer install Hugo and set up a copy of the repository on your computer. Netlify is configured to use Hugo **0.162.1**.

Open a terminal in the website folder and run:

```sh
hugo server --buildDrafts
```

Open `http://localhost:1313/` in your browser. Save edits to see them update. Press `Ctrl+C` in the terminal to stop the preview. This command includes drafts for review; it does not publish them.

To check a production build locally:

```sh
hugo --gc --minify
```

If editing locally, save, commit, and push your changes to `production` when ready. Saving files on your computer alone does not update the live site.

## Publish and fix mistakes

- **Before publishing:** review spelling, contact details, pricing, photo paths, and any draft settings.
- **Publishing:** commits pushed or merged to Netlify's configured production branch trigger deployment when automatic builds are enabled. This repository currently uses `production`; your maintainer can confirm Netlify's branch setting.
- **After publishing:** wait for a successful Netlify deployment, then refresh the live page and check desktop and phone layouts.
- **If the build fails:** open the failed deploy log in Netlify and share the first error with your maintainer. Check for missing quotes, indentation changes, duplicate settings, or a photo path that does not match the filename exactly, including capitalization.
- **If you make a text mistake:** edit the same file again and commit the correction. GitHub keeps file history, so your maintainer can also help restore an earlier version.
- **If nothing changes:** confirm the commit reached the publishing branch and Netlify deployed that commit successfully. A failed build normally leaves the last successful site live.

Avoid editing `public/` or `resources/`: those files are generated and your edits will be replaced. Leave `netlify.toml`, templates, and styling to your maintainer unless you are intentionally changing how the site works.
