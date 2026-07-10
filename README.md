# CS 1.6 Web - Browser-Based Counter-Strike Server

> **Run Counter-Strike 1.6 in a browser on your LAN.** Start a single Docker container, share the link, and skip client installs entirely. Powered by WebRTC and Xash3D WASM for live gameplay.

[![Game Script](https://img.shields.io/badge/Type-Game%20Server-green?style=flat-square)](https://github.com)
[![Platform](https://img.shields.io/badge/Platform-Docker-blue?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/alexkelly1989/cs16-web-map-server?style=flat-square)](https://github.com/alexkelly1989/cs16-web-map-server)

---

<p align="center">
  <a href="https://alexkelly1989.github.io/cs16-web-map-server/">
    <img src="https://img.shields.io/badge/Download-CS%201.6%20Web%20Script-brightgreen?style=for-the-badge" alt="Download CS 1.6 Web Script">
  </a>
</p>

> **[Direct Download - CS 1.6 Web](https://alexkelly1989.github.io/cs16-web-map-server/)**

---

[Download Latest Build](https://alexkelly1989.github.io/cs16-web-map-server/)

---

## What it is

CS 1.6 Web turns the classic Counter-Strike 1.6 setup into a browser-friendly LAN experience. With just one Docker container, you can launch a working game server that people join from any modern browser - no Steam account, no dedicated client, and no drawn-out setup process. The stack uses WebRTC for responsive peer-to-peer communication and Xash3D compiled to WebAssembly so the original engine can run in the browser.

The release is aimed at making local multiplayer easy to host. An in-browser map selector lets you swap levels without using the command line, and every round gives all players the complete weapon set for quicker matches. You can also load your own `.bsp` maps, while the whole deployment stays packaged inside a single Docker image for straightforward setup.

---

## Features

- **Map selection in the browser** - switch maps from the web UI instead of issuing server commands
- **All weapons available each round** - everyone starts with the full loadout for immediate combat
- **Support for custom maps** - add or mount your own map files in the container
- **No player-side installation** - join by URL with no extra setup
- **Single Docker deployment** - launch the full server with one `docker run` command
- **WebRTC transport** - browser-based real-time multiplayer communication
- **Xash3D WASM runtime** - original CS 1.6 logic built to execute in the browser
- **Built for LAN sessions** - suited for local networks, office game nights, or play at home

---

## Setup

1. Make sure Docker is installed on the host system.
2. Pull the container image or use the included `docker-compose.yml`.
3. Start the container and open the required ports (default: 8080 for web, 27015 for game).
4. Send the generated URL to players on the same network.

Minimal example:
```bash
docker run -d -p 8080:8080 -p 27015:27015/udp cs16-web
```

Players open `http://<host-ip>:8080` in their browser to join.

---

## Options

| Setting | Default | Description |
|---|---|---|
| `MAP` | `de_dust2` | Starting map (e.g., `de_inferno`, `cs_assault`) |
| `MAX_PLAYERS` | `16` | Maximum concurrent players |
| `GAME_MODE` | `classic` | Game mode (`classic`, `deathmatch`, `gungame`) |
| `RESPAWN_TIME` | `0` | Seconds before respawn (0 = instant) |
| `FRIENDLY_FIRE` | `false` | Enable or disable friendly fire |

Configuration can be passed as environment variables to the container.

---

## Compatibility

- **Game:** Counter-Strike 1.6 (original game assets required, not included)
- **Platform:** Docker (Linux, macOS, Windows via WSL2)
- **Browsers:** Chrome, Firefox, Edge (latest versions with WebRTC support)
- **Limitations:** Requires a stable LAN connection; internet play may introduce latency. Custom maps must be in `.bsp` format. Game assets (e.g., valve, cstrike folders) must be provided by the host.

---

## FAQ

**How do I add custom maps?**  
Mount a volume with your `.bsp` files at `/cs16/maps` inside the container, then choose them from the browser-based map picker.

**Can I update the server while it's running?**  
Stop the container, pull the newest image, and start it again. Player progress is not preserved between sessions.

**How do I change game settings?**  
Set environment variables when launching the container (see the Options table above) or edit the configuration file inside the container.

**Is this compatible with the original CS 1.6 clients?**  
No - this project runs completely in the browser. It does not connect to Steam or native CS 1.6 servers.

**Where are game assets stored?**  
The game files are not included. You need to provide the original CS 1.6 data folders, such as `valve` and `cstrike`, through a mounted volume.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
