# tv.osgeo.nl
Website en meer t.b.v. OSGeonl TV zoals De Grote Geo Show

## Gemaakt met Hugo

In het kort:

Hugo is een statische website builder, zie https://gohugo.io/.

De site wordt gehost op GitHub als Github Pages in repo: https://github.com/osgeonl/tv.osgeo.nl/
Bijzonderheden: 

* ipv `gh-pages` Branch staat statische/gegenereerde site in `docs` map
* in `docs/` staat ook `CNAME` bestand
* in DNS bij osgeo.nl Provider de `CNAME` naar `osgeo.github.io` staat


Thema van Castanet, voorbeeld: https://sample-castanet.netlify.com/ (werkt nu nog niet, onderzoeken)

https://gohugo.io/getting-started/quick-start/

```bash

$ brew install hugo

$ git clone https://github.com/osgeonl/tv.osgeo.nl tv.osgeo.nl.git

# aanmaken in map tv.osgeo.nl.git 
$ hugo new site tv.osgeo.nl.git

# voeg thema van Castanet toe als submodule
$ git submodule add https://github.com/mattstratton/castanet.git themes/castanet

# Eerst test met "Ananke" thema
$ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
$ echo 'theme = "ananke"' > config.toml

# voeg toe in config
$ echo 'theme = "castanet"' > config.toml

# test: eerste "post"                                   
$ hugo new posts/my-first-post.md
# voeg wat tekst toe in content/posts/my-first-post.md

# Server draaien                 
$ hugo server -D

# Aanpassen config.toml om naar /docs te publiceren  

baseURL = "https://tv.osgeo.nl/"
languageCode = "nl-nl"
title = "De Grote Geo Show"
theme = "ananke"
publishDir = "docs"

# Deploy script deploy.sh
#!/bin/sh

# If a command fails then the deploy stops
set -e

printf "\033[0;32mDeploying updates to GitHub...\033[0m\n"

# Build the project.
# hugo - if using a theme, replace with `hugo -t <YOURTHEME>`
hugo -t ananke

# Go To Public folder
# cd docs

# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site $(date)"
if [ -n "$*" ]; then
	msg="$*"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin master

```
