
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod
echo "theme = 'papermod'" >> hugo.toml

# Deploy

hugo
git subtree push --prefix public origin gh-pages

