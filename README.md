# branch-follow-tag

## Use case

Keep a branch always referencing to the most recent tag.

## Inputs

| Input      | Description |
| ----------- | ----------- |
| GITHUB_TOKEN      | Automatically provided token, that can be used to authenticate on behalf of the GitHub action, with permissions limited to the repository that contains your workflow       |
| SSH_PRIVATE_KEY   | Deploy key for push. Must be set in the repository settings. This is used by the action to push the fast-forwarded branch/commit/PR.        |
| BRANCH | Name of the branch. | 

## Workflow YML

The Action must be run `on:push:tags` triggers to keep the labels up-to-date and run the fast-forward on command. 

```yml
name: Fast-Forward

on: 
  push:
    tags:

jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: APN-Pucky/branch-follow-tag@main
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          SSH_PRIVATE_KEY: ${{ secrets.GH_SSH }}
          branch: stable
```

## Examples

* https://github.com/APN-Pucky/smpl_util
