# MAJU mobile layout patch

Based on the uploaded `style(1).css` and `index(1).html` (renamed to their actual repository filenames).

- `style.css`: add mobile-only responsive overrides for directories, headings, forms, modal, calendar, navigation and overflow. Replace decorative star emoji with an inline SVG drawn using four crossed lines, avoiding iOS emoji substitution. Keep the existing art-school styling and palette.
- `index.html`: version the CSS and JS URLs to refresh cached assets after deployment.

No changes to `app.js`, Firebase configuration, security rules or stored records.
