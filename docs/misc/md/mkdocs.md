---
title: MkDocs
description: Introduction to MkDocs
---

## Why MkDocs ?

MkDocs is probably the fastest **and** easiest way to generate HTML from your notes. 

## How to use MkDocs ?

```bash title="How to get a render in seconds"
# install MkDocs
apt install mkdocs

# Create a new project
mkdocs new my-project
cd my-project

# Preview your render in real time on http://localhost:8000
mkdocs serve

# Render your finished project
mkdocs build
```

The only other thing you need to do is to customize the config file after creating your project.

```yml title="mkdocs.yml" linenums="1"
site_name: My site
site_url: https://mysite.com

nav:
    - My page: page.md
    - My other page: other.md
```

That is literally it. You now have a professional-grade documentation website ready to be put online. 
