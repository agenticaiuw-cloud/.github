# Contributing to Hivemind Cloud

How we work, short version.

## Before you start

* Turn on two factor authentication with an authenticator app (Settings, then Password and authentication). You can add a passkey or security key after. The org won't let you in without two factor. It also blocks accounts that still have text message codes, even as a backup.
* Everyone in Cloud can read every repo. You can only push to your own team's repo and the shared docs repo.
* To get the code on your laptop, use GitHub Desktop, VS Code or the GitHub CLI. Sign in with the GitHub account that joined the org. Use that account on github.com too. Signed out or signed in as anyone else, you get a 404 page for club repos. The first time, each tool opens github.com and asks you to authorize it. That page names the account. Make sure it's the one that joined. With the CLI, run `gh auth login` once. It also gives you a code to enter there. Both are fine because you started them yourself. Then run `gh repo clone agenticaiuw-cloud/platform` with your team's repo in place of platform. Only enter a code the CLI or VS Code shows you. Classic personal access tokens are blocked here. Fine grained ones need Anand's approval.
* In GitHub Settings under Emails, turn on "Keep my email addresses private". That page shows your noreply address, which ends in @users.noreply.github.com.
* In every club repo you clone, set your git email to that noreply address before your first commit. In a terminal, first go into the repo folder, like `cd platform`. Then run `git config user.email "123456+yourname@users.noreply.github.com"` with your own address from that page. In VS Code, open Terminal, then New Terminal. It starts in the repo folder. In GitHub Desktop, open Repository, then Repository Settings, then Git Config. Pick "Use a local Git config", set Email to that address and click Save. This only changes club repos. Your class repos stay as they are. Every commit keeps its email forever and these repos may go public one day.
* Keep club code in club repos. Don't copy it into your own repos while it's private.
* GitHub Actions is off in every repo for now. If your team needs it, ask Anand.

## Making a change

1. Make a branch off main with a short name, like `gateway-retry-logic`. Never commit straight to main.
   * On github.com, pick "Create a new branch for this commit" in the commit box. Editing more than one file? Open the pull request after the first commit. Then switch to your new branch in the branch menu before you edit the next one. The pull request updates on its own.
   * In GitHub Desktop, switch to main and pull. Then click Current Branch, then New Branch.
   * In a terminal, run `git switch main` and `git pull`. Then run `git switch -c gateway-retry-logic`.
2. Keep commits small and clear.
3. Push your branch. Then open a pull request that says what changed and how you tested it.
   * On github.com, there's nothing to push. The commit box takes you to the pull request.
   * In GitHub Desktop, click Publish branch. Then pick Create Pull Request from the Branch menu.
   * In a terminal, run `git push -u origin gateway-retry-logic`. Then open the link it prints.
4. Ask a teammate to review it (Anand for the docs repo). Add them under Reviewers and post the link in your team's thread. Don't merge until someone approves. Asked for changes? Commit them to the same branch and push again. The pull request updates on its own. On github.com, switch to your branch in the branch menu before you edit.
5. Once it's approved, click Squash and merge. That turns your commits into one commit on main. If GitHub lets you pick that commit's email, keep your noreply address. GitHub deletes the branch for you. Your next change starts over at step 1 with a new branch.
6. Never force push to main or delete someone else's branch. Committed or pushed to main by mistake? Don't try to undo it. Say so in your team's thread.

## Working with other teams

Each team builds in its own repo. That way all three teams can work at the same time. You can't push to another team's repo. You can still read it, open issues and comment.

* Need something from another team's code? Open an issue in their repo that says what you need and why. That team decides how to build it.
* Have feedback on another team's work? Comment on their pull request. Only that team merges it.
* Changing how two teams' code fits together? Write a proposal in the docs repo first and add a reviewer from each of those teams.
* The security team reviews every team's work. Expect their comments on your pull requests too.

## Never commit secrets

No API keys, tokens, passwords, private keys or .env files in any repo or Discord message, ever. Keep keys in a local .env file, which every repo's .gitignore already skips. Keep key files you download, like a service account JSON, outside the repo folder. If your code needs the file, put its path in your .env. On github.com, never upload a .env file or a folder that has one. To show teammates which keys the code needs, commit a .env.example file with the key names and no values. A new file doesn't show up in your changes? Its name may match a line in the .gitignore. Ask in your team's thread before you rename it, add it with `git add -f` or change the .gitignore.

If a key ends up anywhere it shouldn't, like a commit, a Discord message, an issue or an AI tool, DM Anand on Discord right away so we can cancel it and make a new one. Tell him where it is, not the key itself. If it's your own key, cancel it yourself first. Deleting or editing it out doesn't make it safe. Don't force push to fix it.

## Found a security problem?

Don't put it in an issue, a pull request or your team thread. DM Anand on Discord. Review comments about a pull request's own changes are fine. Our [security policy](https://github.com/agenticaiuw-cloud/.github/blob/main/SECURITY.md) has the rest.

## AI tools

AI help is welcome. If you use GitHub Copilot, turn off "Allow GitHub to use my data for AI model training" in your Copilot settings (click your profile picture). Turn off training in any other AI tool you use with club code too. That keeps club code out of training data. Never paste secrets or user data into any AI tool and don't let one open your .env file. Many coding agents read files without asking. If yours can block files, block .env.

## Questions

Ask in your team's thread on Discord.
