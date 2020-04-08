# tv.osgeo.nl
Website en meer t.b.v. OSGeonl TV zoals De Grote Geo Show

## Gemaakt met Hugo

Hugo is een statische website builder.

https://gohugo.io/getting-started/quick-start/

Thema van Castanet, voorbeeld: https://sample-castanet.netlify.com/

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



```
castanet