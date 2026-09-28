# NCP-AIN Certification Guide — companion site and free lab guide

Companion website for *NCP-AIN Certification Guide: NVIDIA AI Networking with Spectrum-X and InfiniBand* by Vakeesan Thevarajah (CCIE #43898), published by Cloudfoxy Ltd.

**Live site:** https://cloudfoxy-ltd.github.io/ncp-ain-guide/

What's on the site:

- **Free hands-on lab guide:** Labs 0–13 on NVIDIA Air (free trial) and an ibsim InfiniBand simulator. You can read it online or download it as a PDF.
- **Lab files:** Air topology JSON, the ibsim topology, and OpenSM partitions.
- **Flashcards:** a CSV you can import into Anki or Quizlet.
- **Free sample chapter** of the book.
- **Errata:** you can report a problem with the *Erratum* issue template.

## Repository layout

| Path | What it is |
|---|---|
| `site-src/` | Markdown source of the site (MkDocs `docs_dir`) |
| `site-src/labs/` | Lab pages and pre-rendered figures (`img/`) |
| `site-src/lab-files/` | Topology and config files used by the labs |
| `site-src/downloads/` | PDF of the lab guide |
| `docs/` | **Built site**, served by GitHub Pages. Don't edit it by hand. |
| `mkdocs.yml` | Site configuration (Material for MkDocs) |
| `.github/ISSUE_TEMPLATE/` | Erratum issue form |

## Publishing

In the repo, go to Settings → Pages → *Deploy from a branch*, then choose `main` and `/docs`.

## Rebuilding the site

```bash
pip install mkdocs-material
mkdocs serve      # preview at http://127.0.0.1:8000
mkdocs build      # writes the site into docs/
```

Commit `site-src/` and `docs/` together.

## Licences

- The lab guide text and figures are under [CC BY-NC-SA 4.0](LICENSE). You may share and adapt them non-commercially with attribution.
- The lab files and code snippets are under the [MIT licence](LICENSE-CODE).
- The book itself is **not** covered by these licences. It is © Cloudfoxy Ltd, all rights reserved.

NVIDIA, Spectrum-X, InfiniBand, Cumulus and NVIDIA Air are trademarks of their respective owners. This is an independent study resource that is not affiliated with or endorsed by NVIDIA.
