# PXVIRT / Proxmox VE for ARM64 inside container

Powered by [PXVIRT](https://docs.pxvirt.lierfang.com/en/README.html), a forked of Proxmox VE that support multiple CPU architectures, developed and maintained by [Lierfang](https://www.lierfang.com/).

## Quick Start
> [!Important]
> Do not enable DHCP when create LXC, config IP inside the LXC instead, for example: `dhclient eth0`<br>
> For latest arm64 LXC template: https://images.linuxcontainers.org/images/

#### With `docker run`:
> [!Note]
> - Remove `--detach` if you want an interactive console, to escape, hold CTRL then press P + Q
> - Run `docker attach pxvirt-1 ` to reattach later if needed
```bash
docker run --detach -it --name pxvirt-1 --hostname pxvirt-1 \
    -p 2222:22 -p 3128:3128 -p 8006:8006 \
    --restart unless-stopped  \
    --cgroupns=private \
    --security-opt seccomp=unconfined \
    --security-opt apparmor=unconfined \
    --security-opt systempaths=unconfined \
    --cap-add=SYS_ADMIN \
    --cap-add=NET_ADMIN \
    --cap-add=SYS_MODULE \
    --cap-add=IPC_LOCK \
     --cap-add=SYS_PTRACE \
    --device-cgroup-rule='a *:* rwm' \
    -v /usr/lib/modules:/usr/lib/modules:ro \
    -v /sys/kernel/security:/sys/kernel/security \
    -v ./VM-Backup:/var/lib/vz/dump \
    -v ./ISOs:/var/lib/vz/template/iso \
    -e PASSWORD=123 \
    ghcr.io/longqt-sea/proxmox-ve-arm64
```
Replace `./ISOs` with the path to your ISO folder.

Default root password: `123`

Access the web UI at https://Docker-IP:8006 (accept the self-signed cert).

---

#### With Docker Compose:

`compose.yml`
```yml
services:
  pxvirt-1:
    image: ghcr.io/longqt-sea/proxmox-ve-arm64
    container_name: pxvirt-1
    hostname: pxvirt-1
    restart: unless-stopped
    stdin_open: true
    tty: true
    cgroup: private
    device_cgroup_rules:
      - "a *:* rwm"
    cap_add:
      - SYS_ADMIN
      - NET_ADMIN
      - SYS_MODULE
      - IPC_LOCK
      - SYS_PTRACE
    security_opt:
      - seccomp=unconfined
      - apparmor=unconfined
      - systempaths=unconfined

    # Port mapping only required for Docker Desktop or remote access from other machines.
    ports:
      - "2222:22"
      - "3128:3128"
      - "8006:8006"

    volumes:
      - /usr/lib/modules:/usr/lib/modules:ro        # Required for loading kernel modules
      - /sys/kernel/security:/sys/kernel/security   # Optional, needed for LXC
      - ./VM-Backup:/var/lib/vz/dump                # Shared storage for VM/LXC backups
      - ./ISOs:/var/lib/vz/template/iso             # Shared storage for ISO files

    # Set your own password here
    environment:
      - PASSWORD=123
```

Bring it up:
```
docker compose up -d
```

Default root password: `123`

To attach to the console:
```
docker attach pxvirt-1
```
To escape, hold CTRL then press P + Q

Access the web UI at https://Docker-IP:8006 (accept the self-signed cert).
