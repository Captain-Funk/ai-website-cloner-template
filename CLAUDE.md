@AGENTS.md

## CAPTAIN Ecosystem Context

> Forked from [JCodesMore/ai-website-cloner-template](https://github.com/JCodesMore/ai-website-cloner-template). Customized for CAPTAIN.

- **Team:** The Forge (business tooling)
- **Project:** The War Room — business operations, client site analysis
- **Config key:** `cloner` in `~/.claude/captain.config.json`
- **Category:** tool (forked third-party)

## Cross-Repo Rules

- **Reference but not update.** When working in this repo, you can READ from other CAPTAIN repos via captain.config.json. Never WRITE to another repo from a session focused here.
- **Branch strategy:** `master` stays synced with upstream via rebase. All CAPTAIN customizations go on the `captain` branch.
- **After fresh clone:** Run `bash ~/Projects/captain-plugin/hooks/bootstrap.sh` to restore hookify symlinks.

## Upstream Tracking

- **Upstream:** https://github.com/JCodesMore/ai-website-cloner-template.git
- **Sync:** `git fetch upstream && git checkout master && git rebase upstream/master && git checkout captain && git rebase master`
