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

### Material for MkDocs

If you are wondering why didn't I put any links to the [MkDocs documentation](https://www.mkdocs.org/getting-started/), you have the right reflexes. 

The answer is because I strongly recommend using the Material for MkDocs theme, so you should directly start learning that instead.
The page you're currently looking at was rendered with this theme. 

[:simple-materialformkdocs: Get started with Material for MkDocs](https://squidfunk.github.io/mkdocs-material/){ .md-button .md-main }

#### Quality of life enhancements

If you are using [:material-microsoft-visual-studio-code: Visual Studio Code](https://code.visualstudio.com/), you can add two modules that will greatly enhance your experience.

##### YAML by RedHat

Download YAML by RedHat and paste the following in the JSON settings in order to have the **official** Material for Mkdocs debug:

```json
{
    "yaml.schemas": {
        "https://squidfunk.github.io/mkdocs-material/schema.json": "mkdocs.yml"
    },
    "yaml.customTags": [ 
        "!ENV scalar",
        "!ENV sequence",
        "tag:yaml.org,2002:python/name:material.extensions.emoji.to_svg",
        "tag:yaml.org,2002:python/name:material.extensions.emoji.twemoji",
        "tag:yaml.org,2002:python/name:pymdownx.superfences.fence_code_format"
    ]
}
```

##### TODO Highlight v2

Download TODO Highlight v2 to highlight all the `TODO:` tags in my files. It's an easy way to keep in mind all the options that need to be customized befor you start writing your documentation.

#### Insiders

If you are as hooked as me regarding Material, you will probably buy the sponsor version Insiders. 
When you will need a cheet sheet with the main premium features in one place, take a look at my [Material for MkDocs configuration example](https://flaghunter01.github.io/mkdocs-yml/en/guide/useage.html).
