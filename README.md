# Hugo theme archetype issue

Hey what's good.  I'm having issues creating new posts based on archetypes provided by the theme.  Enclosed is a self-contained repository demonstrating the issue.

The files in `content/test/` are the output of `hugo new` with various hugo versions and options.  The suffix denotes the hugo version used.  If the filename contains `"with-switch"`, it was generated with `hugo new -k test test/<...>`.

## Installation

This repository was created in the following manner:

* `hugo new site hugo-theme-archetype-issue`.
* `hugo new theme test-theme`.
* Add `theme = "test-theme"` to `config.toml`.
* Create `themes/test-theme/archetypes/test.md`.

Two different `hugo` binaries were used.  To install the one responsible for the `0.19` files, run `brew install hugo`.  To install the one responsible for the `master` files, run `go get -u -v github.com/spf13/hugo`.

## Reproduction

To reproduce the issue, run the following:

```
hugo new test/test-0.19.md
hugo new -k test test/test-with-switch-0.19.md
$GOPATH/bin/hugo new test/test-master.md
$GOPATH/bin/hugo new -k test test/test-with-switch-master.md
```

## Expected output

In all cases, I would expect the output files to contain `title`, `date`, and `blurb` in the front matter.
