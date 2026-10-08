# Frequently asked questions

## Can every product run on QBox with TGIANN?

Not unchanged. Smoking is TGIANN-wired; Yacht storage and optional Diving gear use ox\_inventory; Pausemenu uses generic ox-style exports and K9 sniff needs an appropriate item source. Select compatible integrations or implement/test adapters.

## Does the package include clinic maps and sounds?

No Vet clinic MLO or custom K9 ogg files is present. The configured points/names do not install assets. Rockstar base-game assets are referenced by native name. Smoking icons/definitions are missing from this source archive.

## Are the scripts modified by this documentation?

No. SQL/snippets are reproduced as references, not automatically applied. Required external bridges and fixes are documented rather than silently invented.

## Can I use commands anywhere?

A command can open a UI while server actions still enforce roles, proximity, active state and progression. Read the product gates and source reference.

## Does a config language setting translate everything?

Many products include da/en, but hardcoded/server-specific strings can remain. Pausemenu/Smoking do not have a generic Locale switch. Translate source/config text where needed.

## Why do config changes not reset taxes/stock/ownership?

Some config values seed SQL or are fallbacks. Existing saved rows can take precedence; do not delete them just to change a default.

## Is this published on GitBook already?

This deliverable is the GitBook-ready Markdown/navigation package. Publishing requires importing or connecting it to your GitBook space. No online space was created or modified in this task.
