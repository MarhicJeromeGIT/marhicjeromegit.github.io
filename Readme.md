

# Blog Workflow

## 1. Create a New Post

Run (replace the filename as needed):

	hugo new content/post/YYYY-MM-DD-title.md

Edit the new file in `content/post/`.

## 2. Preview Locally (Draft Mode)

To preview drafts and unpublished posts:

	hugo server --watch --buildDrafts

Open the local URL Hugo prints (usually http://localhost:1313) in your browser.

## 3. Publish the Post

In your post's front matter, set:

	draft: false

and make sure the date is correct.

## 4. Build the Site

	hugo

This generates the static site in the `public/` directory.

## 5. Commit and Deploy

Force-add the public directory (since it's gitignored):

	git add -f public
	git commit -am "Publish: new post YYYY-MM-DD-title"


Then push to GitHub Pages:

	git subtree split --prefix public -b temp-gh-pages
	git push -f origin temp-gh-pages:gh-pages
	git branch -D temp-gh-pages

## Notes
- You only need to use `--buildDrafts` when previewing drafts locally.
- Only posts with `draft: false` and a valid date will be published.
- Always run `hugo` and commit before deploying.
- If you add images, make sure they're in the right static folder.

---
Theme setup (one-time):

	git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/papermod
	echo "theme = 'papermod'" >> hugo.toml

