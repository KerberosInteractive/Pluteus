# Pluteus

A self-hosted knowledge base built in Go. Organized by project with Markdown doc pages, plain-text notes, code snippets, and bookmarks: cross-referenced, tagged, and full-text searchable. Single binary, SQLite, no JavaScript framework.

---

![Pluteus Preview Shot](./assets/Shot_A.png)

## What it is

Pluteus is a private knowledge management tool built for developers. It organizes your work into **projects**, each containing docs, notes, snippets, and bookmarked links. All the content items are cross-referenceable and full-text searchable.

**Content types:**
- **Docs**: Markdown pages with a tree structure, breadcrumb navigation, and cross-references
- **Notes**: Quick plain-text captures, pinnable
- **Snippets**: Syntax-highlighted code blocks with language tagging
- **Links**: External bookmarks with descriptions and tags

**Cross-reference syntax** (inside any doc):
- `[[doc:slug]]` / `[[note:id]]` / `[[snippet:id]]` : inline link with hover preview
- `![[note:id]]` / `![[snippet:id]]` : embed content inline
- Full-text search across all content types

---

## Running Pluteus

1. Download `pluteus.exe` from [Releases](../../releases)
2. Place it anywhere and run it
3. Open `http://localhost:8080` in your browser
4. Complete the first-run setup to create your admin account
5. Optional: if simply testing, you can turn on the test data generation
6. Check the `Help` section to find tips, Mardown syntax cheat sheet, and glyph browser

That's it. A `pluteus.db` and supportive files are created in the same directory on first run.

---

## VirusTotal Report

_Check the [VirusTotal report here](https://www.virustotal.com/gui/file-analysis/YTVlMDhiZWM2Y2EzMWFiMGNhMjUyYmVlZDg3NjhjOWY6MTc3NTI5NDM5MA==)_

*MaxSecure* has lovingly dinged Pluteus with a false-positive for "_Trojan.Malware.300983.susgen_". This alarmed me initially, because the release here is generated from a GitHub action from the private repository - no "human" hands touch the release output. I did research on this, and it turns out *MaxSecure* is notorious for being the odd one in the bunch that flags many files with this, including old CD-ROM game files from 1999! Feel free to dive and throw the Pluteus executable at anything else; I just wanted to point this out and share it.

It's worth a bit of research if you're a developer yourself, as this sort of thing could very well pop up for you as well. When trying to assure your users, point out that while the initial list of AV checks is great for at-a-glance (_and where most users stop_), the "Details" and "Behavior" tabs are where the real details are at, with the Behavior section being the most important in my opinion.

Other elements on the Behavior tab of the report worth calling out the "_Memory Pattern Domains_"; there are some odd URLs there and in other places that seenm to have no place being in Pluteus! The reason they show up is simple: those are various links and information contained within the test seed data. During the initial setup of Pluteus, users have the option of enabling demo/sample data generation, in the event they want to quickly see how a more mature content library would look. Nothing nefarious, though this was another waving red flag that alarmed me when I was doing a security audit. I wasted far too much time investigating this stuff, because I had forgotten about the demo data!

---

## Configuration

Pluteus is configured via environment variables. No config file needed.

| Variable | Default | Description |
|---|---|---|
| `PLUTEUS_PORT` | `8080` | HTTP server port |
| `PLUTEUS_DB_PATH` | `./pluteus.db` | Path to the SQLite database file |

Example:
```
PLUTEUS_PORT=9000 PLUTEUS_DB_PATH=D:\data\pluteus.db pluteus.exe
```

---

## Requirements

- Windows x64
- A modern browser

No installation, no runtime, no external services.

---

## Planned Features

- Linux/Mac support
- Images!
- Video embedding (_YouTube, Vimeo, etc_)
- 

---

## Built with

- [Go](https://go.dev)
- [HTMX](https://htmx.org)
- [SQLite](https://sqlite.org) via [modernc.org/sqlite](https://pkg.go.dev/modernc.org/sqlite) (pure Go, no CGO)
- [Goldmark](https://github.com/yuin/goldmark) for Markdown rendering
- [highlight.js](https://highlightjs.org) for syntax highlighting

---

## License

GNU General Public License v3.0
