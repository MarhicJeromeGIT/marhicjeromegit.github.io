
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod
echo "theme = 'papermod'" >> hugo.toml

# Deploy

hugo
git subtree push --prefix public origin gh-pages


# New post
hugo new content content/post/2025-10-15-october-update.md

# Run hugo (draft mode)
hugo server -D