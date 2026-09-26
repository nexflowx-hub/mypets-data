# MyPets Digital Library — Cover & Round Brand Seal System

**Version:** 1.0  
**Reviewed:** 2026-09-25  
**Applies to:** all guide covers, library hero cards, print/PDF covers and selected printable worksheets.

## Canonical production asset

- Media ID: `mypets-round-logo`
- Frontend source: `src/lib/brand.ts#BRAND.logoUrl`
- The production frontend currently points that brand field to the official Cloudinary logo asset.
- The cover system must consume the brand/media reference instead of hard-coding a second logo copy.

## 1. Brand mark


Use the **current official round MyPets logo / medallion** from the project brand assets.

Do not:
- reconstruct the logo from text;
- substitute an emoji/paw icon;
- redraw it from memory;
- crop it into a new shape;
- distort the circular proportion.

If the final production asset is not yet wired into the frontend, keep the component/API slot ready and use the canonical official file once available.

## 2. Cover placement

Default:
- bottom-right;
- safe margin: 4% of the shortest cover edge;
- visible but secondary to title and hero image;
- do not overlap the animal's face, eyes, paws or an important focal point.

Web/editorial card:
- round seal opacity: approximately 0.82;
- may include a subtle embossed/medallion treatment if it remains faithful to the official mark.

Print/PDF cover:
- full-colour or approved brand version at normal opacity;
- optional secondary watermark version at 0.12–0.18 opacity.

## 3. Internal-page watermark

Use sparingly.

Recommended only for:
- printable worksheets;
- posters;
- challenge calendars;
- trackers;
- standalone diagrams likely to be shared outside the reader.

Default:
- bottom-right;
- 0.10–0.16 opacity;
- never behind small body text;
- never reduce readability.

## 4. Cover hierarchy

1. MyPets collection/kicker
2. Guide title
3. Short subtitle
4. Hero photograph/illustration
5. Round MyPets seal
6. Optional guide number / collection marker

The campaign message **1 eBook = 1 kg de ração** may appear as a restrained footer/ribbon, but should not overpower the editorial title.

## 5. Image treatment

Prefer:
- real dog photography;
- natural expression;
- strong eye contact when appropriate;
- enough negative space for title;
- editorial crop rather than stock-advertising look.

Avoid:
- distressed/sick-looking animals as generic cover decoration;
- exaggerated sad imagery;
- overly staged studio props;
- text over a visually busy face.

## 6. Consistency across the collection

Each guide may use a different hero image, but the collection should share:
- same title grid;
- same seal location;
- same corner radius / cover ratio;
- same typographic hierarchy;
- same MyPets collection marker.

## 7. Accessibility

The seal itself is decorative when the page already contains the MyPets brand name:
- HTML alt should be empty in that context.

If the seal is the only visible brand identifier:
- accessible label: "MyPets".

## 8. Export

For print/PDF:
- preserve vector logo when possible;
- do not rasterize at low resolution;
- keep safe margins;
- ensure watermark does not disappear in grayscale printing.

## 9. Reader integration

The exact cover configuration per guide is defined in:

`media/media-placement-master.json`

The frontend should implement one reusable `GuideCover` component driven by this configuration.
