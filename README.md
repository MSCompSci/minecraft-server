# Custom Minecraft Server

## Client Setup
1. Install [Prism Launcher](https://prismlauncher.org/download/windows/) and log in with your Microsoft/minecraft account
2. Download client modpack from this repo
3. Install Java (if needed) following [Prism's guide](https://prismlauncher.org/wiki/getting-started/installing-java/)
4. Add an instance in Prism and import the modpack
5. Launch the instance
6. In minecraft, select multiplayer and add a new server using the server domain name
7. Connect to the server and play minecraft :)

## Server Setup
1. Install [podman](https://podman.io/)
2. Clone this repo to your server
3. Add a forwarding secret to `forwarding.secret` and `FabricProxy-Lite.toml`
4. Add usernames to whitelist and ops list
5. Change MOTD in `velocity.toml`
6. Launch server with `podman kube play mc-server.yaml`
7. After initial install, restart server so it can add the forwarding secret patch

## Backups
1. Stop server with `podman kube play --down mc-server.yaml`
2. Export podman volume with `podman volume export minecraft-data -o ~/minecraft-bk.tar`
3. Compress tarball with `xz minecraft-bk.tar`
4. Restart server with `podman kube play mc-server.yaml`

## Notes:

Data is saved in a podman volume that mounts at `/home/$USER/.local/share/containers/storage/volumes/minecraft-data/_data`

Server can be stopped and removed with `podman kube play --down mc-server.yaml`

Server can be recreated using a new config with `podman kube play --replace mc-server.yaml`

## Credits
- Server and modpack icon by [Emoji Kitchen](https://emojikitchen.dev/)

- The client modpack includes config files from the [Simply Optimized](https://modrinth.com/modpack/sop) modpack.