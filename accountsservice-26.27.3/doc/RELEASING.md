# Making an AccountsService Release

AccountsService uses auto-generated version numbers derived from the commit
metadata of the last git commit. This happens automatically during configuration,
when meson runs the [`generate-version.sh`][./generate-version.sh] file. As such,
you don't need to do any manual version bumps.

The procedure to create a release is as follows:

* Make sure your checkout is up to date

```bash
git pull upstream main
```

* Use the [GitLab UI](https://gitlab.freedesktop.org/accountsservice/accountsservice/-/releases/new)
  to start creating a release

* Generate the version number

```bash
$ bash ./generate-version.sh
25.34.76
```

* Generate a changelog

```bash
$ git shortlog --no-merges $(git describe --abbrev=0)..
Jane Doe (2)
    Commit message
    Another commit message

John Doe (1)
    Reticulate splines
```

* Fill the generated version number into the "Tag Name" field, and allow GitLab
  to create the tag.

    * When prompted, paste in the changelog as the tag's message

* Paste the changelog as the release's message

* Confirm the creation of the release

* Done!
