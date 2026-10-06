# Shira Vansover-Hager — blue headings and muted rose links

A simple, responsive, two-section academic website built with plain HTML and
CSS. No JavaScript, external fonts, frameworks, installation, or build step.

## This revision

All links use the existing muted rose (`#916276`), including the advisor link,
email address, conference names, [arXiv] links, and equal-contribution stars.
Links turn dusty blue on hover, keyboard focus, or activation. A subtle
underline stays visible on ordinary links at rest and becomes clearer on
interaction; keyboard focus also has an outline.

“Spotlight presentation” and “Oral presentation” are ordinary dark text in
italics, not rose or bold. The words “to appear” and venue punctuation are
also neutral.

There are now two equal-level blue section headings:

- Publications & preprints
- Workshop papers

The smaller “Conference Papers” subtitle has been removed, and “Workshop
papers” is a separate section rather than a nested subtitle. Existing fonts,
biography, photo controls, horizontal divider, titles, author order, venue
wording, and link destinations are preserved. No new publication claims or
paper URLs have been added.

## Preview

Extract the ZIP and double-click `index.html` inside the extracted folder.
Keep these files together:

```text
shira-website-blue-rose-refined/
├── index.html
├── styles.css
├── assets/
│   ├── photo-placeholder.svg
│   └── favicon.svg
├── .nojekyll
└── README.md
```

## Update your existing website

Back up your current files, then replace **both `index.html` and `styles.css`**.
The new section structure is in the HTML; link and distinction colors are in
the CSS. Keep your current photograph and other assets; the two supplied SVG
assets are unchanged from the preceding version.

Before replacing files, carry over your image's `src` and `alt`, personal text
edits, CV/profile links, and any customized photo size, zoom, or crop settings.
Preserve unrelated repository files and domain settings. For a new site,
upload the contents of this folder with `index.html` at the publishing root,
not the ZIP or an extra enclosing folder. Use the GitHub Pages setup from the
previous version.

## Add your photo

Put your picture at `assets/photo.jpg`. In `index.html`, find `PHOTO:` and
change the existing image's attributes to:

```html
src="assets/photo.jpg"
alt="Shira Vansover-Hager"
```

For a PNG, use `photo.png` in both the filename and the `src`. Match filename
capitalization. The image is cropped to a 4:5 frame without stretching.

Near the top of `styles.css`, adjust the existing photo controls:

```css
--photo-width: 10rem;
--photo-width-mobile: 6rem;
--photo-zoom: 1;
--photo-x: 50%;
--photo-y: 50%;
```

Keep zoom at least `1`. For a closer crop, try `--photo-zoom: 1.15`.
A smaller Y percentage, such as `35%`, favors the upper part of the image.
The smallest-screen rule uses a narrower photo frame automatically.

## Edit your text and links

Open `index.html` in a plain-text editor. The `ABOUT`, `PHOTO`, `RESEARCH`,
and `WORKSHOPS` comments mark the main editing areas.

When changing the email, update both its visible text and its `mailto:`
value. A commented CV link is provided in `profile-links`; upload a public
CV to `assets/cv.pdf` and uncomment it to enable the link. Review any CV or
photograph for private information before publishing.

No real photo, CV, phone number, or unconfirmed profile address is bundled.
All source asset paths are relative, so the same folder structure can be
used at a site root or within a project path.

## Add a paper or preprint

Copy a complete `<li class="paper">...</li>` block into the first section's
`paper-list` for a publication or preprint, or into the workshop section's
list for a workshop paper. Replace the title, author list, venue, and link.

Each paper title uses an `<h3>` beneath its section's `<h2>`. Give the paper
title a unique `id` and use the same value in `article aria-labelledby`.
Update any link's `aria-label` so it describes the correct paper.

For a new preprint, a metadata block can look like this after replacing both
placeholders with the actual values:

```html
<div class="paper-meta">
  <p class="venue">Preprint, YEAR</p>
  <p class="paper-links"><a href="ACTUAL_PAPER_URL">arXiv</a></p>
</div>
```

The stylesheet adds the square brackets around arXiv. Do not type a second
pair into the HTML. No empty preprints subsection is shown by default.

A conference entry with a presentation distinction uses:

```html
<p class="venue"><a class="venue-link" href="https://icml.cc/Conferences/2025">ICML 2025</a>, <em class="distinction">Spotlight presentation</em></p>
```

The conference link is rose; the italic distinction is dark. All existing
conference and arXiv destinations were carried over from the previous
version, without changing or re-verifying publication statuses. The Mirror
Descent entry still has only a conference link; its paper URL was not
supplied. There is a commented-out paper link ready for a real URL.

## Colors and fonts

The variables at the top of `styles.css` control the palette:

```css
--accent: #335f8a;         /* Name and section headings */
--secondary: #916276;      /* Muted rose */
--link: var(--secondary);  /* All links at rest */
--link-hover: var(--accent);
--text: #293442;           /* Body and italic distinctions */
--secondary-soft: #dfcbd3; /* Subtle horizontal divider */
```

The font stacks still start with Book Antiqua for headings and paper titles,
and Calibri for body text. Browsers use the next available font when those
are not installed, so the exact font can vary across computers and phones.
No font files or external font requests are included.

The single `<hr class="section-divider">` remains between the introduction
and the first paper section. Its default thickness is `1px`. To adjust the
gap before Workshop papers, change `.research + .research` in the CSS.

## Checks performed

The supplied design was rendered in headless Chromium at widths from 280 to
1920 pixels, with additional checks at 200% root text sizing. The phone
preview uses a separate mobile/touch context at a 390-pixel viewport.
Checks passed for horizontal overflow, equal section-heading levels and
colors, link colors at rest/hover/keyboard focus, plain italic distinctions,
placeholder loading, unique IDs, internal links, reduced-motion behavior,
and unchanged biography, paper text, URLs, font stacks, and photo controls.

The test browser blocks local file URLs, so the exact supplied stylesheet
and SVG assets were embedded in an in-memory copy of the HTML for rendering.
The distributed HTML retains normal relative asset paths, which were also
checked for file existence. Actual devices and every browser engine have
not been tested. The PNG previews are screenshots of the supplied design,
not separately drawn mockups.
