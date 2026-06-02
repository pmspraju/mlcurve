# MLCurve

Machine Learning Insights & Analysis

## About

MLCurve aggregates and analyzes machine learning content from newsletters and research sources.

## Local Development

### Prerequisites

- Ruby (2.7 or higher)
- Jekyll
- Git

### Setup

1. Clone the repository
2. Install dependencies:
```bash
   bundle install
```

3. Run locally:
```bash
   bundle exec jekyll serve
```

4. Visit: http://localhost:4000

## Adding Content

### From Newsletter JSON

1. Place newsletter JSON in `newsletters/` folder
2. Run parser:
```bash
   python alphasignal_parser.py newsletters/your-file.json
```
3. Output will be created in `_posts/`

### Manual Post

Create a file in `_posts/` with format: `YYYY-MM-DD-title.md`

```markdown
---
title: "Your Post Title"
date: YYYY-MM-DD
source: Source Name
layout: post
---

Your content here...
```

### Notes (Auto-Discovery)

Notes live in `_notes/` and are grouped automatically by front matter values.

Recommended path pattern:

- `_notes/<domain>/<topic>/<slug>.md`

Required note front matter fields:

```markdown
---
title: Your Note Title
domain: ml
topic: basics
tags:
   - example-tag
updated: YYYY-MM-DD
---
```

Normalization rules (important):

- Use lowercase values for `domain` and `topic` (example: `ml`, `qc`, `basics`, `transformers`).
- Use lowercase folder names in `_notes/`.
- Use hyphenated lowercase filenames (`attention-mechanism.md`).

The site groups topics case-insensitively, but using lowercase everywhere avoids accidental duplication and keeps URLs/content consistent.

## Deployment

Push to main branch. GitHub Pages will automatically build and deploy.

## Custom Domain

This site uses the custom domain: mlcurve.com

Configure DNS:
- A records → GitHub Pages IPs
- CNAME: www → yourusername.github.io

## License

Content aggregated under fair use for educational purposes.