# linuxkit-builder

## Installation (Development-style)

    nix-build . -A linuxkit-builder
    ./result/bin/nix-linuxkit-configure

It'll write to:

 - ~/.cache/nix-linuxkit-builder/, in particular
   ~/.cache/nix-linuxkit-builder/nix-state/console-ring is interesting
 - ~root/.ssh/ for the SSH config
 - /etc/nix/machines
 - ~/Library/LaunchAgents/org.nix-community.linuxkit-builder.plist


It should automatically start and stay running, but ...


You can force start it with:

    launchctl start org.nix-community.linuxkit-builder

You can force stop it with:

    launchctl stop org.nix-community.linuxkit-builder

If after you stop it you may want to check for processes, like:

    pgrep vpnkit
    pgrep linuxkit
    pgrep hyperkit

If something goes wrong and it didn't stop propery, you can try:

    pkill -F ~/.cache/nix-linuxkit-builder/nix-state/hyperkit.pid hyperkit
