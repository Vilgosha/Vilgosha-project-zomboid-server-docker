# 🧟 Project Zomboid Dedicated Server

A Dockerized Project Zomboid dedicated server using the `renegademaster/zomboid-dedicated-server` image.

### 🔗 Image References

| Resource | Link |
|----------|------|
| Docker Hub | https://hub.docker.com/r/renegademaster/zomboid-dedicated-server |
| GitHub | https://github.com/Renegade-Master/zomboid-dedicated-server/tree/main |

> The GitHub page is the primary reference for supported environment variables, image tags, and known issues. Check it when updating the server or troubleshooting.

---

## 📁 Repository Structure

```
.
├── docker-compose.yaml          # Container definition
├── .env.example                 # Template for secret environment variables
├── environment-reference.md     # Description of every environment variable
├── ZomboidDedicatedServer/      # Server binaries (auto-downloaded, not committed)
└── ZomboidConfig/               # Server config, saves, and logs
    └── Server/
        ├── ZomboidEE.ini        # Main server config
        ├── ZomboidEE_SandboxVars.lua  # Sandbox/difficulty settings
        └── ZomboidEE_spawnpoints.lua  # Spawn point definitions
```

---

## 🚀 Getting Started

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-folder>
```

### 2. Set up secrets

```bash
cp .env.example .env
```

Edit `.env` and fill in your passwords:

```env
ADMIN_PASSWORD=your_admin_password
SERVER_PASSWORD=your_server_password
RCON_PASSWORD=your_rcon_password
```

> ⚠️ `.env` is gitignored and must **never** be committed.

### 3. Start the server

```bash
docker compose up -d
```

On first run, the image will automatically download the Project Zomboid dedicated server via SteamCMD. This may take several minutes.

### 4. Check server status

```bash
docker compose ps
docker compose logs -f
```

Wait until you see `SERVER STARTED` in the logs before attempting to connect.

---

## ⚙️ Configuration

Server settings are stored in `./ZomboidConfig/Server/ZomboidEE.ini` on the host (mounted into the container). Edit the file and restart the server to apply changes.

```bash
docker compose restart
```

See [`environment-reference.md`](./environment-reference.md) for a full description of all environment variables.

### Key settings at a glance

| Setting | Value | Notes |
|---------|-------|-------|
| Game version | `public` | Stable branch |
| Max players | `2` | Edit `MAX_PLAYERS` in compose |
| Primary port | `16261/udp` | Default PZ port |
| RCON port | `27015/tcp` | |
| VAC | enabled | Via Steam |
| Pause when empty | `true` | Saves CPU when no one is online |
| Autosave interval | `10 min` | |
| Max RAM | `4096m` | |
| Timezone | `UTC+3` | |

---

## 🌐 Connecting

In the Project Zomboid main menu: **Join → Add Server**

| Field | Value |
|-------|-------|
| Host | `<your-server-ip>` |
| Port | `16261` |
| Password | *(your `SERVER_PASSWORD`)* |

---

## 🖥️ RCON (Remote Console)

RCON allows you to run admin commands without attaching to the container.

```bash
# Using docker exec
docker exec -i zomboid rcon-cli --port 27015 --password "$RCON_PASSWORD" <command>

# Example: send a message to all players
docker exec -i zomboid rcon-cli servermsg "Server restarting in 5 minutes!"

# Kick a player
docker exec -i zomboid rcon-cli kickuser "<username>"
```

---

## 🔧 Common Operations

### Stop the server
```bash
docker compose down
```

### Restart the server
```bash
docker compose restart
```

### View live logs
```bash
docker compose logs -f
```

### Update the server
```bash
docker compose pull
docker compose up -d
```

The container will automatically update the game files via SteamCMD on startup when `GAME_VERSION=public`.

### Backup saves

```bash
tar -czf zomboid-backup-$(date +%Y%m%d).tar.gz ./ZomboidConfig
```

---

## 📂 Data & Persistence

| Host path | Container path | Contents |
|-----------|----------------|----------|
| `./ZomboidDedicatedServer` | `/home/zomboid/ZomboidDedicatedServer` | Game server binaries |
| `./ZomboidConfig` | `/home/zomboid/Zomboid` | Saves, config, logs, mods |

Both directories are created automatically on first run. Add them to `.gitignore` to avoid committing large binary or save files.

---

## 🔒 Security Notes

- Never commit `.env` or any file containing passwords to version control
- Use `STEAM_VAC=true` to enable anti-cheat on public servers
- Restrict `BIND_IP` to a specific interface if the host has multiple network interfaces
- Change the default `ADMIN_PASSWORD` before exposing the server publicly

---

## 📜 License

This repository contains server configuration only. Project Zomboid is property of [The Indie Stone](https://projectzomboid.com).
