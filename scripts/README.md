# Scripts

This directory contains helper scripts used for working with the public documentation site `rabs-public`.

## `publicpush.js`

Generates a stripped documentation version of the project and serves it via Docsify.

### Usage

```bash
node ./scripts/publicpush.js
```

By default, the output is placed in a sibling directory named `rabs-public` relative to the repository root. The script will:

1. Remove existing contents of the destination (except any `.git` folder).
2. Copy files from the current repository while removing code. Lines containing the marker `// {K}` are kept to provide context.
3. Create `index.html` and a dynamic `_sidebar.md` for Docsify.
4. Commit and push any changes in `rabs-public` to its remote repository.
5. Serve the docs locally on port `3005` using `npx serve`.

Ensure you have Node.js installed and that `npx` is available in your PATH. The `rabs-public` folder should be initialised as a Git repository and have a remote configured.
