# zt

Browse, create, and attach to remote Zellij sessions.

`zt` is a tiny wrapper around `ssh`, `mosh`, and `zellij` for remote machines where
you keep long-running terminal work inside Zellij sessions.

Defaults:

- Host: `tmm`
- Transport: `ssh`
- Picker: `fzf` when available, numbered prompt otherwise

Install:

```bash
git clone https://github.com/yogevkr/zt.git
ln -sf "$PWD/zt/zt" ~/.local/bin/zt
```

Usage:

```bash
zt                 # browse sessions on tmm
zt list            # list sessions
zt main            # attach/create session main
zt new work        # attach/create session work
zt close work      # close a running session
zt kill work       # kill session work
zt delete work     # close and delete saved session state
zt --mosh main     # attach/create over mosh
zt -H mac-mini     # browse another host
```

Environment:

```bash
export ZT_HOST=tmm
export ZT_TRANSPORT=ssh # or mosh
```

Requirements:

- Python 3
- `ssh`
- `zellij` on the remote host
- `fzf` locally, optional
- `mosh` locally and remotely, optional

License: MIT
