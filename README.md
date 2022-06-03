# workflows
Bunch of re-useable workflows

## Auto labeler
.github/workflows/auto_label.yml

This workflow will automatically label a PR with the appropriate labels based on the number of files changed within the PR.

You must define the labels to use and these labels must exist in your repo for adding to PRs

Three break points are defined:
- Less than 10 files changed: `Small`
- Between 10 and 50 files changed: `Medium`
- More than 50 files changed: `Large`

TODO:
- Make the breakpoints configurable
- Determine label based off combination of files changed and number of lines changed
- Better error handling
- Handle more PR states than opened.

Example use:
```yml
name: Auto label PRs with size

# Run only when PR opened
on:
  pull_request:
    types: [ opened ]

jobs:
   call-label-workflow:
    uses: saasaTom/workflows/.github/workflows/auto-label.yml@1c8c328091c41934f3907894481b40d2b65cffb2 #main
    with:
      small_label: 🤩 small pr
      medium_label: 😅 medium pr
      large_label: 🙃 large pr
```