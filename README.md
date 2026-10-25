# Uzman Ali: academic website

One self-contained page (`index.html`) with no build step.

```
academic-site/
├── index.html        ← the whole site
├── photo.jpg         ← headshot (square, ~640×640)
├── cv-academic.pdf   ← "Academic CV" button
├── cv-industry.pdf   ← "Industry résumé" button
├── logos/            ← optional institution logos
└── figures/          ← (create) research-card figures
```

## 1. Photo, PDFs, logos and figures
- **Photo:** replace `photo.jpg` and keep the filename.
- **PDFs:** replace `cv-academic.pdf` / `cv-industry.pdf` and keep the filenames.
  ⚠️ Both current PDFs contain your phone number, home postcode and referees' contact details. Before publishing, export versions without them.
- **Logos:** save e.g. `logos/tau.svg`. In `index.html`, find a monogram such as
  `<span class="logo" aria-hidden="true">TAU</span>` and replace the text with
  `<img src="logos/tau.svg" alt="" loading="lazy">`.
- **Figures:** in the *Research themes* section, replace a `<div class="figure-ph">…</div>` with
  `<img src="figures/sar-map.jpg" alt="Simulated SAR in a head model" loading="lazy">` (16:9 works best).

## 2. Add a publication or news item
Open `index.html` and search for `SITE_DATA`.

**News:** add a line at the **top** of `news`:
```js
{ year: "2026", isNew: true, text: "Paper accepted in <em>IEEE TAP</em>." },
```

**Publication:** copy any entry in `publications` and edit it:
```js
{
  id: "J4", type: "journal", year: 2027,              // journal | conference | review | chapter
  authors: ["Uzman Ali", "Abdul Basir", "Toni Björninen"],
  title: "…",
  venue: "IEEE Trans. Antennas Propag.", venueFull: "IEEE Transactions on Antennas and Propagation",
  volume: "", number: "", pages: "",
  doi: "10.1109/…", url: "", pdf: "", oa: "", award: "",
  tags: ["implant", "sar"],                           // drives research-card paper counts
  featured: false, takeaway: ""
},
```
Numbering, grouping, year filters, BibTeX and research-theme counts update automatically.
Set `featured: true` (and write a `takeaway`) to show a paper in *Selected publications*. Keep three featured.
Also update “Last updated …” in the footer.

## 3. Deploy on GitHub Pages
1. Create a public repo, e.g. `uzmanali22.github.io` (that name gives you `https://uzmanali22.github.io`).
2. Upload everything in this folder (Add file → Upload files) and commit to `main`.
3. Open repo **Settings → Pages**.
4. Under *Build and deployment*, choose **Deploy from a branch**, then branch `main`, folder `/ (root)`, and save.
5. Wait 1–2 minutes and open the URL. Then replace every `https://YOUR-SITE-URL/` in `index.html` (canonical, Open Graph, JSON-LD) with the real address.

*Netlify alternative:* drag this folder onto app.netlify.com/drop.
