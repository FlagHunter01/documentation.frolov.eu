---
title: GitHub
description: Basics of working with GitHub from the command line
---



Set up GitHub on your local Linux machine to work from the command line.

## Requirements

- A Linux client
- A [GitHub account](https://github.com/signup)

## Sources

- [GitHub Docs](https://docs.github.com/en/get-started)

## Guide


This is a quick summary of [Get started](https://docs.github.com/en/get-started) by GitHub.
It's aim is to help you start working with a GitHub repo ASAP, not to explain Git in great detail. 

I highly recommend reading [About Git](https://docs.github.com/en/get-started/using-git/about-git) and [Hello World](https://docs.github.com/en/get-started/start-your-journey/hello-world). 

!!! info "GitHub CLI"
    GitHub CLI offers additional functionalities for interaction with GitHub (e.g. Issues). 
    ==I do not use it at this time==. However, it is required to authenticate in order to sync with GitHub repos. 

### Setup

```title="Install Git"
apt install git
``` 

```title="Provide mandatory information"
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

```title="Install GitHub CLI" linenums="1"
type -p curl >/dev/null || apt install curl -y
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& apt update \
&& apt install gh -y
``` 

```title="Authenticate with GitHub"
gh auth login
```

!!! info "Visual Studio Code"
    VSCode's UI allows you to do everything we'll do here. It should also detect that you're using Git if you open the associated folder and offer Git actions in the third left menu. 

    To associate with VSCode, use the following magic:
    ```
    git config --global core.editor "code --wait"
    ```

### Cloning a repo

 - Go to [GitHub](https://github.com/), open the wanted repository and click on the green `<> Code` button. 
 - Select `HTTPS` and copy the URL. 
 - Return to your terminal, navigate to the folder you want your repo to appear and enter the clone directive:

```linenums="1"
git clone <URL you copied>
cd <repo name>
```

### Working with changes

```title="Create a branch"
git branch <branch>
```

```title="Open a branch"
git checkout <branch>
```

```title="Stage a changed file"
git add <file>
```

```title="Add staged changes into Git history"  
git commit -m "<commit message>"
```

```title="Check current change status"
git status
``` 

### Interacting with the remote repo

```title="Synchronize local codebase with remote"
git pull <remore URL> <branch>
```

```title="Synchronize remote with changes made locally"
git push <remote URL>
```

!!! failure "non-fast-forward error"
    If your local copy is behind the remote, you won't be able to push your changes. 
    In order for it to work,  `git pull` first.

