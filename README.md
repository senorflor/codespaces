# codespaces

Testing out codespaces

## Notes

### Trial 1 (https://github.com/senorflor/codespaces/commit/302f5928defec0c28af6ee6186b7446c67489413)

- Startup (ubuntu base image, no other config) is quite slow
- Editing a buffer works pretty well (that's where I'm updating this README.md in fact!)
- Terminal seems unusably slow (10s of seconds of delays). Will retest once there's actually a project.
- Git repo by default cloned to `/root/workspace/codespaces` since no config.

### Trial 2 (Same code version)

- Terminal is now much more responsive. Most likely local explanation (based on past experience/correlation only; didn't look at direct evidence and nothing was amiss in Activity Monitor) is some kind of pathological state in Chrome at the time of the test. Also noticed the repo creation screen responding _incredibly_ slowly to some basic interactions right before this issue (e.g. checking the Initialize with README.md checkbox being so slow the render wasn't catching it until I changed some other state on the page).
- Note for both trials: SSH key forwarding is properly set up for main account by default: able to interact with GitHub/`origin` remote without any intervention.
- I had an old fork of necolas's `dotfiles` checked out from when I created my own dotfiles repo (github.com/senorflor/tilde), and this was automatically picked up, copied into the dev container in the codespace, and symlinked to `~` (`/root/` in this case) as expected from Codespaces docs. Will delete in future trials for purposes of testing fallback/repo-specific dotfiles config.
- Additional files that are created in `~` besides symlinked dotfiles:
    - .vs-liveshare-keychain (JSON file of liveshare credentials. TODO: explore liveshare on Codespaces instances later)
    - .vs-liveshare-settings.json (1000ms SyncRpcTelemetryTresholdMs; BTW, is this key misspelled?)
    - .vscode-remote (as is set up in VS Code remote sessions from desktop; includes installed extensions, server, etc.)
    - .wget-hsts (probably from downloading the vscode remote stuff at startup time)

### Trial 3 (https://github.com/senorflor/codespaces/commit/28f53331240e0a0a6dafccfd9c5c29f51f9d1af4, also renamed old dotfiles repo)

- Dotfiles persisted; restarted session by choosing "Codespaces: Disconnect". Going to close tab and delete codespace from GitHub UI now instead.

