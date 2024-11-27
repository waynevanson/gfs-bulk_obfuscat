# Notes

Bro get your notes out.

## Resources

1. [Git hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)

## Workflow

So looks like we're going to hook into the following.

1. gitattributes
2. post-commit
3. pre-push
4. merge commits

### `.gitattributes`

1. Create filter in git config for `split`.
2. Add the pattern to git attributes.

### `post-commit`

WE could still use git attributes for splitting parts, but we need post commit to commit those parts.

When we **commit** a big file, we need to split it into smaller files and commit those one by one instead.

We commit each part separately otherwise we cannot upload, as remote git providers throttle pack size (what gets uploaded).

1. Check size of each file in commit.
2. If one is bigger than the max file size, split it and put the parts into `.git/parts/<file-path>.part.aaa` (26 x 26 x 26 = 17,576 - almost a terabyte) should be enough parts per file.
3. commit each part
4. remove main file.
