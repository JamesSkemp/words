# blog
Blog replacement, running [Hugo](https://gohugo.io/).

## Adding a new post

First, start Hugo, if you want to preview the content as you write it.

```
..\hugo.exe server
```

> If you want to preview drafts pass the `--buildDrafts` parameter.

Next create a new file in the **content\post** directory. Use the awesome [Dillinger](http://dillinger.io/) as needed.

```
..\hugo.exe new post/post-name.md
```

Once you're okay with the content, stop Hugo by pressing **Ctrl + C**.

Generate the site by running `..\hugo.exe`.

Add the new post file to Git, as well as the newly generated/updated files.

Update the **gh-pages** branch.

```
git subtree push --prefix public git@github.com:JamesSkemp/words.git gh-pages
```

## Post title to creation script

Within LINQPad, run the following:

```
var title = "Post Title Here";

title = title.ToLower().Trim()
	.Replace(" ", "-")
	.Replace(":", "-")
	.Replace("+", "-")
	.Replace("(", "-")
	.Replace(")", "-")
	.Replace("--", "-")
	.Replace("--", "-")
	.Replace("--", "-")
	;

(@"..\hugo.exe new post/" + title + ".md").Dump();
```
