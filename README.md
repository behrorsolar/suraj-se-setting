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
README.md           This editing guide (optional)
.gitignore          Local file exclusions (optional)
```

The top-level `index.html` must sit beside `styles.css`, not inside another folder. Extract the prepared upload ZIP first; upload its contents, not the ZIP file itself.

This replaces the previous generated version. Remove the old `build.mjs`, `check.mjs`, `server.mjs`, `site-content.mjs`, `project-assets.json`, `package.json`, `assets/` and `dist/` from GitHub. Keep original reference screenshots, review images and backup ZIPs out of the public repository. A backup of the previous local website was saved separately before conversion.

## One-time Cloudflare change

Use your existing **Cloudflare Pages** project, connected to this GitHub repository. Under the project's build settings, replace the old `npm run build` and `dist` settings:

| Setting | Value |
| --- | --- |
| Framework preset | None |
| Build command | `exit 0` |
| Build output directory | `.` (a single dot, meaning the repository root) |
| Root directory | Leave blank |
| Production branch | `main`, or your repository's actual production branch |
| Automatic production branch deployments | Enabled |

Save these settings before committing the replacement files to the production branch. If the files were already committed, retry the deployment after saving the settings. Keep your existing custom domain connection.

Cloudflare supports plain static HTML and automatically deploys GitHub changes:
- https://developers.cloudflare.com/pages/framework-guides/deploy-anything/
- https://developers.cloudflare.com/pages/configuration/git-integration/

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

- Phone: **9911488881**; call links use `tel:+919911488881`.
- WhatsApp: `https://wa.me/919911488881` (with a prefilled enquiry message).
- Email: **behrorsolar@gmail.com**.
- Headquarters: Alwar — https://www.ggenergy.in/
- Regional office: Behror–Neemrana — https://behrorsolar.in/
- Bhiwadi city office: coming soon.

Change these in both pages and in every related contact link. Company experience figures (558 installations, 2,672 kWp) are explicitly company-wide totals from the supplied PM Surya Ghar listing, not Bhiwadi-only totals. Review them when newer figures are available.

The primary domain is https://www.globalgreenenergy.co.in. If changing the domain, update the canonical and alternate links in both HTML pages, `robots.txt` and `sitemap.xml`. If adding a new page later, add its public address to `sitemap.xml`.
