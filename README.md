# zt

Remote Zellij session manager for humans and automation.

`zt` is a tiny wrapper around `ssh`, `mosh`, and `zellij` for remote machines where
you keep long-running terminal work inside Zellij sessions.

Defaults:

- Host: `tmm`
- Transport: `ssh`
- Picker: `fzf` when available, numbered prompt otherwise

Running `zt` with no subcommand opens the interactive browser. Automation should
always pass a subcommand such as `list`, `status`, `exists`, `ensure`,
`attach --background`, `close`, or `delete`.

Install:

```bash
git clone https://github.com/yogevkr/zt.git
ln -sf "$PWD/zt/zt" ~/.local/bin/zt
```

Usage:

```bash
zt                 # browse sessions on tmm
zt --version
zt list            # list sessions
zt list --json     # machine-readable session list
zt status --json   # machine-readable dependency check
zt exists main     # exit 0 if active, 1 if missing
zt ensure main     # create detached session if missing
zt main            # attach/create session main
zt new work        # attach/create session work
zt attach main --background --json
zt close work      # close a running session
zt kill work       # kill session work
zt close work --missing-ok --json
zt delete work     # close and delete saved session state
zt delete work --missing-ok --json
zt --mosh main     # attach/create over mosh
zt -H mac-mini     # browse another host
```

Environment:

```bash
export ZT_HOST=tmm
export ZT_TRANSPORT=ssh # or mosh
export ZT_CONNECT_TIMEOUT=10
export ZT_REMOTE_PATH='/opt/homebrew/bin:/usr/local/bin:$HOME/.cargo/bin:$HOME/.local/bin:$PATH'
```

Useful flags:

```bash
zt --no-input list --json
zt --connect-timeout 3 status --json
zt --ssh-option StrictHostKeyChecking=accept-new list
zt attach main --print-command
zt ensure main --print-command
```

Requirements:

- Python 3
- `ssh`
- `zellij` on the remote host
- `fzf` locally, optional
- `mosh` locally and remotely, optional

License: MIT
