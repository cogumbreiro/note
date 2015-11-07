# Install Coq's syntax-highlighting for Gedit

```
mkdir -p ~/.local/share/gtksourceview-3.0/styles &&
( cd ~/.local/share/gtksourceview-3.0/styles &&
  [ -f coq_style.xml ] || curl -L -O https://github.com/coq/coq/raw/trunk/ide/coq_style.xml )

mkdir -p ~/.local/share/gtksourceview-3.0/language-specs &&
( cd ~/.local/share/gtksourceview-3.0/language-specs &&
  [ -f coq.lang ] || curl -L -O https://github.com/coq/coq/raw/trunk/ide/coq.lang )

mkdir -p ~/.local/share/mime/packages

update-mime-database ~/.local/share/mime
```
