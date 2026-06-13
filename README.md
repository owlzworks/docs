# docs

Static, public documents for owlzworks apps, served via GitHub Pages.

Layout: **`<project>/`** per app, then per concern.

```
<project>/
  version.json          # app-version manifest (update gate)
  legal/                # Privacy Policy & Terms of Service (en/ko) + index
    index.html
    privacy_en.html  privacy_ko.html
    terms_en.html    terms_ko.html
```

## offlens

| document | URL |
|---|---|
| Version manifest | https://owlzworks.github.io/docs/offlens/version.json |
| Privacy (en / ko) | https://owlzworks.github.io/docs/offlens/legal/privacy_en.html · `…/privacy_ko.html` |
| Terms (en / ko) | https://owlzworks.github.io/docs/offlens/legal/terms_en.html · `…/terms_ko.html` |

### version.json schema

| field | type | meaning |
|---|---|---|
| `latestVersionCode` | int | newest build — installs **below** this get an optional "update available" prompt |
| `latestVersionName` | string | human version shown in that prompt |
| `minSupportedVersionCode` | int | minimum allowed build — installs **below** this get a blocking "update required" gate |
| `storeUrl` | string (optional) | link the Update button opens; defaults to the app's Play Store page |

Bumping `version.json` takes effect on the next app launch (GitHub Pages CDN ~10 min);
the app treats an unreachable file as up-to-date. The legal HTML is generated from
`packages/client/tools/{gen_legal.py,legal_content.json}` in the app repo — edit there,
regenerate, and copy the `dist/` output into `offlens/legal/`.
