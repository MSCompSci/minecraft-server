# Custom Minecraft Server

## Setup
1. Install [podman](https://podman.io/)
2. Copy `mc-server.yml` to a new folder
3. Uncomment options for server name, MOTD, icon, ops, and whitelist
4. Add custom values
5. Launch server with `podman kube play mc-server.yml`

## Backups
1. Stop server with `podman kube play --down mc-server.yml`
2. Export podman volume with `podman volume export minecraft-data -o ~/minecraft-bk.tar`
3. Compress tarball with `xz minecraft-bk.tar`

## Notes:

Data is saved in a podman volume that mounts at `/home/$USER/.local/share/containers/storage/volumes/minecraft-data/_data`

Server can be stopped and removed with `podman kube play --down mc-server.yml`

Server can be recreated with new config with `podman kube play --replace mc-server.yml`

## Credits
- Server icon from [Emoji Kitchen](https://emojikitchen.dev/)
