# SOGo6-docs

Documentation for SOGo 6 webmail: for admins who deploy and set up SOGo, and for developers.
Written in AsciiDoc, built with [Antora](https://antora.org).

## Layout

| Folder            | Antora component | Content                                  |
|-------------------|------------------|------------------------------------------|
| `landing/`        | `SOGo6-Home`     | Welcome page (site start page)           |
| `admin/`          | `SOGo6-AdminDoc` | Admin documentation                      |
| `developer/`      | `SOGo6-DevDoc`   | Developer documentation                  |
| `supplemental-ui/`| —                | Header, styles added to the default UI   |

Pages are in `<component>/modules/ROOT/pages/`, the menu in `<component>/modules/ROOT/nav.adoc`.

## Build

Requirements: [Node.js](https://nodejs.org) 24 (with npm) and git. Run from the repo root:

```sh
npm ci                                # installs Antora (pinned in package.json) into node_modules/
npx antora antora-playbook.yml        # builds the site into build/
```

- `npm ci` is only needed once, and again when `package-lock.json` changes.
- The build downloads Antora's default UI on first run, then reuses it from `.cache/`.
- `antora-playbook.yml` builds the checked-out branch of this folder, uncommitted changes
  included.

To view the result, open `build/index.html` in a browser, or serve the folder (links work
better over HTTP), for example:

```sh
npx http-server build -p 8080 -c-1    # then open http://localhost:8080
```

"Edit this Page" links: in a local build they open the local file (`file://…`). When the
build runs with `CI=true` (publishing server, CI job) they point to the file on GitHub, on the
branch being built (`edit_url` in the playbook).
