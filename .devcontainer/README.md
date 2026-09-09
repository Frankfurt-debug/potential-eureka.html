# GUI desktop in a GitHub Codespace

A Codespace is a Linux container with no GUI by default. The `desktop-lite`
devcontainer feature in `devcontainer.json` adds one.

## Connecting

Rebuild the container, then:

- **Browser:** open forwarded port 6080 in the Ports tab -> noVNC -> Connect ->
  password `vscode`.
- **Native VNC client:** `gh codespace ports forward 5901:5901`, then connect to
  `localhost:5901`. GitHub's forwarded HTTPS URLs won't accept raw VNC/RDP, so
  the CLI tunnel is required.
- **RDP instead of VNC:** install xrdp and forward 3389 the same way. This is
  more setup than desktop-lite.

The desktop is Fluxbox/XFCE. `apt-get install` anything else needed, such as a
browser or file manager.

## Constraints

- No GPU, so software rendering makes video and 3D slow.
- Codespaces idle-stop after about 30 minutes.
- Only `/workspaces` survives a container rebuild.
- GitHub's Acceptable Use Policy restricts Codespaces to development use.
