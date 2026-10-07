# Studio website (GitHub Pages)

One site for all your apps. These files are copied to a **separate public
repository** named `<username>.github.io` (see `docs/release-checklist.md`).
This folder is only the source; nothing in the app reads it.

## Layout

```
index.html                    studio home page, lists the apps
style.css                     shared look (light and dark)
app-ads.txt                   one line, covers every app (needs the AdMob publisher id)
dangle/index.html             app page
dangle/privacy-policy.html    privacy policy of Dangle
templates/                    NOT published: copy for each new app (do not upload)
```

Every app gets its own folder with its own `privacy-policy.html`
(`/<app>/privacy-policy.html`). Never share one policy between apps: each must
describe what that app really does.

## Placeholders to replace everywhere

| Placeholder | Replace with |
|---|---|
| `{{STUDIO}}` | your studio / brand name |
| `{{EMAIL}}` | the public contact e-mail |
| `{{PUB_ID}}` | AdMob publisher id, `pub-0000000000000000` (AdMob → Settings → Account information); only in `app-ads.txt` |

On a computer with a terminal, from this folder:

```
sed -i 's/{{STUDIO}}/My Studio/g; s/{{EMAIL}}/hello@example.com/g' index.html dangle/*.html templates/*.html
sed -i 's/{{PUB_ID}}/pub-0000000000000000/' app-ads.txt
```

Or use the editor's find-and-replace before pasting the files into GitHub.

## Publishing

1. Create the GitHub account (brand name, brand e-mail) and the **public**
   repository `<username>.github.io`.
2. Upload these files (not `templates/` and not this README) to the repository
   root, keeping the folders.
3. Settings → Pages → *Deploy from a branch* → `main` / `(root)`.
4. Check in a private window: `/`, `/app-ads.txt`, `/dangle/privacy-policy.html`.
5. Use `https://<username>.github.io/dangle/privacy-policy.html` as the privacy
   policy URL in Play Console and in the app (`lib/app_info.dart`).
