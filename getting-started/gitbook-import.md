# Connect this package to GitBook

The package contents are the repository root. Keep README.md, SUMMARY.md, .gitbook.yaml and gitbook-docs.yaml together at that root.

## Site-wide Git Sync

1. Copy this package's contents into the documentation repository.
2. Connect that repository and branch from GitBook's Git Sync panel.
3. Leave **Project directory empty** when these files are at the repository root. If you upload the whole outer MM-Store-GitBook folder instead, set Project directory to MM-Store-GitBook.
4. Import Git → GitBook initially and inspect the navigation.
5. Review page covers, hints, tables and code blocks before publishing.

The supplied gitbook-docs.yaml maps one English documentation space to ./, with stable key mm-store-docs. The supplied .gitbook.yaml maps README.md and SUMMARY.md. On an existing site that already has a mapping, preserve its current space key instead of replacing it with this new starter key: changing a key replaces the space and can break links to its existing ID.

If GitBook says gitbook-docs.yaml does not exist, check the selected branch and Project directory. .gitbook.yaml alone is the space config, not the site config.

## Branding

Follow [visual setup](visual-setup.md). Repository content includes the cover, hierarchy and page styling; the published site's colors, navigation logo, fonts and theme are applied through GitBook Customization. The local preview does not change online settings.

Official references:

- [Content configuration](https://gitbook.com/docs/docs-as-code/git-sync/content-configuration)
- [Site-wide monorepos and Project directory](https://gitbook.com/docs/docs-as-code/git-sync/monorepos)
- [Theme customization](https://gitbook.com/docs/guides/customizing-your-site/how-to-customize-your-sites-theme)

This deliverable prepares the files. It does not push a repository, edit a signed-in GitBook site or publish it.
