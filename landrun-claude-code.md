# Sandbox Claude Code with Landrun

This pearl uses landrun to sandbox Claude Code agents to only be able to read and write from certain directories.

![](/shots/landrun-claude-code.png)

>[!WARNING]
>Highly experimental.

## Requirements

* [Landrun](https://github.com/Zouuup/landrun)
* [Claude Code](https://github.com/anthropics/claude-code)


```bash
#!/bin/sh

landrun --unrestricted-network --ldd \
			       --add-exec \
			       --env TERM \
			       --env HOME \
			       --env PATH \
			       --ro /etc/ssl/certs \
			       --ro /etc/ssl \
			       --ro /etc/host.conf \
			       --ro /etc/nsswitch.conf \
			       --ro /etc/hosts \
			       --ro /etc/resolv.conf \
			       --ro /etc/ld.so.cache \
			       --ro /proc \
			       --ro /dev \
			       --rox /lib64 \
			       --rox /lib  \
			       --rox /bin \
			       --rox /usr/bin \
			       --rw /dev/null \
			       --rw $HOME/.claude \
			       --rw $HOME/.claude.json \
			       --rw $HOME/.local/state/claude \
			       --rw $HOME/.local/share/claude \
			       --rw /tmp \
			       --rwx $PWD \
			       $HOME/.local/bin/claude

```
