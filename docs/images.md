# Images and galleries

Put post and gallery photos beside an `index.md` page (a Hugo page bundle), or in `assets/images/` or `static/images/`. JPEG, PNG, WebP, TIFF, and BMP photos are converted to WebP during the build. Remote images, SVGs, and animated GIFs retain their original format.

The shared image renderer produces 320, 480, 640, 960, 1280, 1600, and 1920 pixel widths, capped at the source width. It never enlarges small originals. `srcset` and `sizes` let the browser select an appropriate file for the layout and device pixel density. Dimensions reserve image space; offscreen images load lazily.

## Blog post

```yaml
---
title: "A family session"
image: "cover.jpg"
image_alt: "Family walking together outdoors"
---
```

Use normal Markdown for images in the post:

```markdown
![Parents holding their newborn](newborn.jpg)
```

The cover loads eagerly on the post page and lazily in the blog index.

## Gallery

Add `{{< gallery >}}` to a page to display its bundled images. For intentional ordering, descriptive alt text, and optional captions, define a gallery:

```yaml
gallery:
  - src: "first.jpg"
    alt: "Couple embracing beside the lake"
    caption: "An evening by the water"
  - src: "second.jpg"
    alt: "Wedding guests celebrating outdoors"
```

Gallery images keep their original proportions. Grids use one column by default, two from 640px, and three from 1024px. Site navigation switches to its desktop layout at 768px.

Use Markdown, front matter images, or the gallery shortcode for this pipeline. Raw HTML `<img>` elements bypass image processing.

## Temporary stock photography

Pexels photos fill services without matching original portfolio images. Sources,
creators where available, download URLs, license links, and page assignments are
recorded in `docs/service-photo-sources.json`. Downloaded originals live in
`assets/images/services/stock-*.jpg`; Hugo generates responsive WebP derivatives.

Pages using these images set `stock_preview: true`. Cards and featured images
identify stock as session inspiration; galleries use “Session Inspiration.”
When replacing stock with Tracey's own matching work, update `image`, `image_alt`,
and `gallery`, remove `stock_preview`, and set `photo_preview: false` for a
matching portfolio gallery. Keep source records current.

## Card focal points

Service and category front matter supports `image_position: "50% 20%"`
(CSS horizontal/vertical object position) and `image_fit: "contain"`.
Use `contain` for close headshots and collages to preserve the entire photograph.
For other photos, set the focal point around the subject and check the card crop.
These settings apply to section cards and individual service cards at every breakpoint.

`image_crop` can select a single frame from an original collage using Hugo's
crop specification (for example `480x400 TopRight`). The original remains intact;
the featured photo is cropped before responsive WebP generation. Review every
crop visually, and adjust `image_alt` to describe the selected frame.
