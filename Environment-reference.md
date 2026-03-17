# Project Zomboid Server — Environment Variable Reference

All environment variables supported by the [`renegademaster/zomboid-dedicated-server`](https://github.com/RenegadeMaster/zomboid-dedicated-server) Docker image.

Values shown are from the current configuration.

---

## 🔐 Admin

| Variable | Your Value | Description |
|----------|------------|-------------|
| `ADMIN_USERNAME` | `admin` | Username of the server administrator account created on first run. |
| `ADMIN_PASSWORD` | *(secret)* | Password for the admin account. **Store in `.env`, never commit.** |

---

## 🪪 Server Identity

| Variable | Your Value | Description |
|----------|------------|-------------|
| `SERVER_NAME` | `ZomboidEE` | Internal server name. Used as the filename prefix for server config and save files in `~/Zomboid/Server/`. |
| `SERVER_PASSWORD` | *(secret)* | Password players must enter to join the server. Leave empty for a public server. **Store in `.env`.** |
| `PUBLIC_SERVER` | `true` | Whether the server is listed in the in-game public server browser. |

---

## 🌐 Network

| Variable | Your Value | Description |
|----------|------------|-------------|
| `BIND_IP` | `0.0.0.0` | IP address the server binds to. `0.0.0.0` means all interfaces. Set to a specific IP to restrict. |
| `DEFAULT_PORT` | `16261` | Primary UDP port for player connections. Must match the published port in `ports:`. |
| `UDP_PORT` | `16262` | Secondary UDP port used for game traffic. Typically `DEFAULT_PORT + 1`. |

### Ports summary

| Port | Protocol | Purpose |
|------|----------|---------|
| `16261` | UDP | Main game connection port |
| `16262` | UDP | Secondary game traffic |
| `27015` | TCP | RCON remote console |
| `8766` | UDP | Steam matchmaking |
| `8767` | UDP | Steam matchmaking (secondary) |

---

## 🎮 Steam

| Variable | Your Value | Description |
|----------|------------|-------------|
| `USE_STEAM` | `true` | Enables Steam integration. Required for Steam authentication and server browser listing. |
| `STEAM_VAC` | `true` | Enables Valve Anti-Cheat (VAC). Bans cheaters detected by Steam's anti-cheat system. |
| `GAME_VERSION` | `public` | Steam branch to run. Options: `public` (stable release), `beta` (unstable). |

---

## 🖥️ RCON

| Variable | Your Value | Description |
|----------|------------|-------------|
| `RCON_PORT` | `27015` | TCP port for RCON connections. Allows remote server command execution. |
| `RCON_PASSWORD` | *(secret)* | Password required to authenticate RCON connections. **Store in `.env`, never commit.** |

---

## ⚔️ Gameplay

| Variable | Your Value | Description |
|----------|------------|-------------|
| `MAX_PLAYERS` | `2` | Maximum number of players allowed on the server simultaneously. |
| `PAUSE_ON_EMPTY` | `true` | Pauses the game simulation when no players are online, preserving resources and preventing the world from ticking unattended. |
| `AUTOSAVE_INTERVAL` | `10` | How often (in minutes) the server saves the world to disk. Lower values reduce data loss on crash but increase disk I/O. |

---

## ⚡ Performance

| Variable | Your Value | Description |
|----------|------------|-------------|
| `MAX_RAM` | `4096m` | Maximum Java heap memory allocated to the server process. Format: `<number>m` (megabytes) or `<number>g` (gigabytes). Increase for larger player counts or more active maps. |

---

## 🕒 System

| Variable | Your Value | Description |
|----------|------------|-------------|
| `TZ` | `UTC+3` | Timezone for the server container. Affects log timestamps. Uses POSIX timezone format. |

---

> **Security tip:** Sensitive variables (`ADMIN_PASSWORD`, `SERVER_PASSWORD`, `RCON_PASSWORD`) should never be hardcoded in `docker-compose.yaml`. Use a `.env` file (see `.env.example`) and add `.env` to `.gitignore`.
