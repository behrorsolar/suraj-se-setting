# Global Green Energy — Bhiwadi

A directly editable HTML and CSS website. No build, framework, package installation or JavaScript is needed. The English and Hindi versions each contain the entire site on one page.

## Files to upload to your GitHub repository

Upload the contents of this folder at the repository's top level. Keep the two folders as folders.

```text
index.html          English page
styles.css          Shared design, colours and spacing
images/             Optimized logo and project photos
hi/index.html       Hindi page
404.html            Page-not-found message
favicon.svg         Browser tab icon
robots.txt          Search engine instructions
sitemap.xml         English and Hindi page addresses
_headers            Cloudflare response headers
wrangler.jsonc      Hosting setup for the existing globalgreenenergy Worker
.assetsignore       Keeps hosting files and local archives out of the website
README.md           This editing guide (optional)
.gitignore          Local file exclusions (optional)
```

The top-level `index.html` must sit beside `styles.css`, not inside another folder. Extract the prepared upload ZIP first; upload its contents, not the ZIP file itself.

This replaces the previous generated version. Remove the old `build.mjs`, `check.mjs`, `server.mjs`, `site-content.mjs`, `project-assets.json`, `package.json`, `assets/` and `dist/` from GitHub. Keep original reference screenshots, review images and backup ZIPs out of the public repository. A backup of the previous local website was saved separately before conversion.

## One-time Cloudflare change

Use your existing **Cloudflare Worker named `globalgreenenergy`**, connected to **`behrorsolar/suraj-se-setting`**. This is a Workers project, not a Pages project. The owner-provided screenshots confirm the repository, Worker name, production branch and current settings. Under **Settings → Build → Build configuration**, use:

| Setting | Value |
| --- | --- |
| Build command | Leave empty; remove `npm run build` |
| Deploy command | `npx wrangler deploy` |
| Root directory | `/`, as currently shown in the dashboard, meaning the repository root |
| Production branch | `main` |
| Disable builds | Off |
| Build watch paths — Include paths | `*`, as currently shown |

Save these settings before committing the replacement files to the production branch. `wrangler.jsonc` and `.assetsignore` must be uploaded beside `index.html` at the top level of the repository. If the HTML files were already uploaded, add these two hosting files and commit them after saving the build settings. That commit starts a deployment. If needed, go to **Deployments → View Build History**, open the latest build and choose **Retry build**.

There is no build output directory field for this Workers setup. The `assets.directory` value in `wrangler.jsonc` points to the repository root. The configuration uses the exact existing Worker name and serves static assets directly, with a custom 404 page and trailing-slash directory URLs such as `/hi/`. No Worker JavaScript file, new Pages project, extra deploy hook, cron job, secret or binding is needed.

Domain routing remains managed in the Cloudflare dashboard: the configuration has no `route` or `routes` field and uses `workers_dev: false`, following Cloudflare's guidance for dashboard-managed routes. Keep the existing `www.globalgreenenergy.co.in` domain connection and existing API token selection. `observability.enabled` preserves Worker logging. `.assetsignore` excludes the hosting configuration, this guide, ZIP archives and the locally extracted upload folder from public website assets.

Cloudflare supports plain static HTML and automatically deploys GitHub changes:
- https://developers.cloudflare.com/workers/ci-cd/builds/configuration/
- https://developers.cloudflare.com/workers/static-assets/binding/
- https://developers.cloudflare.com/workers/wrangler/configuration/

These settings are instructions; they have not been changed in your Cloudflare account from this workspace.

## Everyday updates

1. Edit `index.html` for English text or `hi/index.html` for Hindi text. Comments mark the main sections.
2. Edit `styles.css` for design changes; both pages use the same file.
3. Put new pictures in `images/` and update their image paths in the HTML. Use lowercase filenames without spaces, such as `bhiwadi-rooftop.jpg`.
4. Save your changes to GitHub's production branch with **Commit changes**. If editing on your computer, upload the changed files to GitHub, or commit and push using GitHub Desktop.
5. Cloudflare automatically deploys that commit. Check the deployment is successful before checking the live page.

Saving a file only on your computer does not upload it to GitHub. Uploading a picture makes it available; add or update its HTML image tag to display it on the page. English and Hindi text are edited separately, so update both when a business detail changes.

### Changing a project photo

Find its `<figure class="project-photo">` under the `Projects` comment. Update the `<a href>` (full photo link), `<img src>`, descriptive `alt`, location caption and capacity. Set `width` and `height` to the new photo's actual pixel dimensions. JPG, PNG and WebP files all work. Example:

```html
<figure class="project-photo">
  <a class="project-image-link" href="/images/bhiwadi-rooftop.jpg" target="_blank" rel="noopener noreferrer" aria-label="View photograph: Bhiwadi, 3 kW">
    <img src="/images/bhiwadi-rooftop.jpg" width="1200" height="800" loading="lazy" decoding="async" alt="3 kW rooftop solar installation in Bhiwadi">
    <span class="photo-view">View photograph ↗</span>
  </a>
  <figcaption><h3>Bhiwadi</h3><span>3 kW</span></figcaption>
</figure>
```

Gallery thumbnails crop consistently; clicking them opens the full photo. For a new project, copy an existing complete `<figure>` and replace its details in both language pages. Keep the introductory photo's `fetchpriority="high"`; use `loading="lazy"` for gallery photos.

The combined header logo has transparent margins removed and optimized WebP versions plus a PNG fallback. Keep all three `combined-logo` files unless you update the header's `<picture>` in both pages.

### Contact and offices

- Phone: **9468688811**; call links use `tel:+919468688811`.
- WhatsApp: `https://wa.me/919468688811` (with a prefilled enquiry message).
- Email: **myadav@behrorsolar.in**.
- Headquarters: Alwar — https://www.ggenergy.in/
- Regional office: Behror–Neemrana — https://behrorsolar.in/
- Bhiwadi city office: coming soon.

Change these in both pages and in every related contact link. Company-wide PM Surya Ghar figures are 569 installations and 2,723 kWp installed capacity, based on the owner-supplied vendor listing screenshot dated 30 October 2026. These are not Bhiwadi-only totals. The gallery continues to use four supplied project examples.

The primary domain is https://www.globalgreenenergy.co.in. If changing the domain, update the canonical and alternate links in both HTML pages, `robots.txt` and `sitemap.xml`. If adding a new page later, add its public address to `sitemap.xml`.


## October 2026 website refresh

English and Hindi pages now include the dedicated Bhiwadi call/WhatsApp number 9468688811 and myadav@behrorsolar.in. Desktop floating buttons become a bottom contact bar on small screens. Native HTML links and disclosure elements need no JavaScript.

The sharing preview uses images/bhiwadi-solar-sharing.jpg (1200 × 630, approximately 160 KB). The WebP copy is optional for future use within a page. Do not preload the sharing image or display it as the hero solely for social previews.

### Structured data

Both HTML files contain a JSON-LD graph near the end of the head. It connects:
- Global Green Energy: https://ggenergy.in/#business (the existing Alwar business identifier).
- Behror Solar: https://behrorsolar.in/#organization, with parentOrganization referencing Global Green Energy.
- The Bhiwadi website, its English/Hindi pages and two solar installation services.
- A dedicated Bhiwadi ContactPoint with the new number/email and an explicitly scoped service area.

The shared social profiles belong to the Behror Solar entity, and visible links explain the regional account relationship. No Bhiwadi street address, map pin, business hours or review rating is invented. The company-wide installation figures match the owner-supplied PM Surya Ghar listing. The Bhiwadi office remains marked as coming soon. FAQ content is present without promising a Google FAQ rich result.

Changing a contact or location requires updating visible content and the JSON-LD in both HTML pages. Keep each page’s canonical URL on its own domain; company identity references do not replace canonical URLs.

The other two sites have not been edited by this refresh. For consistency, Behror Solar’s existing Global Green Energy node and parentOrganization reference should use https://ggenergy.in/#business rather than a second company identifier on the Behror domain. Preserve the Behror Solar entity’s existing ID and its own office contact details.

Upload the prepared refresh ZIP contents into the root of the existing GitHub repository and commit to main. Cloudflare keeps the same blank build command, npx wrangler deploy deploy command and / root directory. Saving files locally does not deploy them.
