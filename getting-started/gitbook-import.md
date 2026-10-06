# Import into GitBook

This package has README.md, SUMMARY.md and .gitbook.yaml at its documentation root. Navigation explicitly lists the product guides and reference pages.

## Git Sync route

1. Extract the package.
2. Put the contents of MM-Store-GitBook (not an extra outer folder unless you intentionally map it) into your documentation repository.
3. In your GitBook space, connect the GitHub/GitLab repository using Git Sync.
4. Map the correct directory and choose the initial Git-to-GitBook import direction so these documents become the starting content.
5. Check sidebar hierarchy, code blocks/tables and internal links, then publish through your GitBook account.

The bundled YAML uses root ./, readme README.md, summary SUMMARY.md. If using a docs subfolder, map/set root consistently; avoid paths accidentally repeating docs/docs.

## ZIP import alternative

GitBook also documents multi-page Markdown/HTML ZIP import. Navigation behavior may differ from Git Sync, so check ordering/nesting after import. Git Sync is the preferred route for maintaining this explicit SUMMARY hierarchy.

Official references checked during creation:

- [Content configuration](https://gitbook.com/docs/docs-as-code/git-sync/content-configuration)
- [Git Sync import guide](https://gitbook.com/docs/guides/editing-and-publishing-documentation/import-or-migrate-your-content-to-gitbook-with-git-sync)
- [Content migration/import](https://gitbook.com/docs/getting-started/import)

Account setup, subscription capabilities and publishing are managed in GitBook. This deliverable does not create an online space, sign in or upload to an external repository.
