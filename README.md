<div align="center">

# 🎮 HavocSMP Plugin

[![Minecraft](https://img.shields.io/badge/Minecraft-1.16--1.21.4-brightgreen?style=for-the-badge)](https://www.spigotmc.org/)
[![Java](https://img.shields.io/badge/Java-21-orange?style=for-the-badge&logo=java)](https://www.java.com/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Redis](https://img.shields.io/badge/Redis-Enabled-red?style=for-the-badge&logo=redis)](https://redis.io/)
[![bStats](https://img.shields.io/badge/bStats-29429-00ADD8?style=for-the-badge)](https://bstats.org/plugin/bukkit/29429)

**A powerful, feature-rich server management plugin with cross-server Redis integration**

[Features](#-features) • [Commands](#-commands) • [Installation](#-installation) • [Configuration](#%EF%B8%8F-configuration) • [Building](#-building)

</div>

---

## 📖 Overview

HavocSMP is a comprehensive server management plugin designed for Minecraft networks. It provides essential utilities, player management tools, cross-server communication via Redis, and seamless multi-server support through Velocity/BungeeCord integration.

## ✨ Features

### 🔌 Core Systems
- **MySQL Database** - Persistent data storage for player information
- **Redis Integration** - Real-time cross-server synchronization and caching
- **bStats Metrics** - Anonymous usage statistics for plugin improvement ([View Stats](https://bstats.org/plugin/bukkit/29429))
- **Configurable Messages** - Fully customizable via `messages.yml`
- **Smart Cooldowns** - Command cooldowns with cross-server syncing
- **Permission System** - Fine-grained access control

### 👥 Player Management
- **Command Spy** (`/commandspy`) - Monitor commands with Redis persistence
- **Private Messaging** - DMs, replies, toggles, and blocking
- **Settings GUI** - Interactive player preferences menu
- **Block System** - Block unwanted messages from specific players

### 🎮 Gamemode Management
- Quick gamemode commands: `/gmc`, `/gms`, `/gma`, `/gmsp`
- Change other players' gamemodes with permissions
- Disable specific gamemodes server-wide temporarily

### 🌐 Teleportation & Navigation
- **Player Teleports** - `/tp`, `/tphere` with cooldowns
- **Spawn System** - `/spawn` and `/setspawn`
- **Hub Integration** - `/hub` for quick hub return
- **Server Switching** - `/join <server>` for cross-server navigation

### 📢 Communication & Announcements
- **Alert System** 
  - Local: `/alert chat <message>`
  - Global: `/alert chat -g <message>` (Redis broadcast)
  - Supports chat, title, or both formats
- **Auto Announcements** - Timed broadcasts
- **Chat Control** - `/togglechat` with Redis sync

### 💰 Economy Features
- **Starter Kit** (`/starter`) - One-time kit with 24hr cooldown
- **Withdraw** (`/withdraw`) - Convert balance to physical notes (Vault required)

### ⚙️ Administrative Tools
- Config hot-reload with `/havocsmp reload`
- Update checker and notifications
- Join event management
- Command monitoring across the network

---

## 📋 Commands

<details>
<summary><b>🛠️ Administration Commands</b></summary>

| Command | Aliases | Permission | Description |
|---------|---------|------------|-------------|
| `/havocsmp reload` | `/hsmp` | `havocsmp.admin` | Reload plugin configurations |
| `/alert <type> <message> [-g]` | - | `havocsmp.alert` | Send local or global alert |
| `/update <message>` | - | `havocsmp.update` | Send update notification |
| `/joinevent` | - | `havocsmp.joinevent` | Manage join events |
| `/disabledgamemode <mode>` | `/dgm` | `havocsmp.disabledgamemode` | Toggle gamemode availability |

</details>

<details>
<summary><b>🔨 Moderation Commands</b></summary>

| Command | Aliases | Permission | Description |
|---------|---------|------------|-------------|
| `/vanish` | `/v` | `havocsmp.vanish` | Toggle vanish mode |
| `/commandspy` | `/cmdspy` | `havocsmp.commandspy` | Toggle command monitoring |
| `/togglechat` | `/tc` | `havocsmp.togglechat` | Enable/disable server chat |

</details>

<details>
<summary><b>💬 Messaging Commands</b></summary>

| Command | Aliases | Permission | Description |
|---------|---------|------------|-------------|
| `/msg <player> <message>` | `/tell`, `/whisper`, `/w`, `/m` | `havocsmp.message` | Send private message |
| `/reply <message>` | `/r` | `havocsmp.reply` | Reply to last message |
| `/msgtoggle` | `/tpm` | `havocsmp.msgtoggle` | Toggle private messages |
| `/block <player>` | - | `havocsmp.block` | Block/unblock player messages |

</details>

<details>
<summary><b>🎮 Gamemode Commands</b></summary>

| Command | Permission | Description |
|---------|------------|-------------|
| `/gmc [player]` | `havocsmp.gamemode.creative` | Set creative mode |
| `/gms [player]` | `havocsmp.gamemode.survival` | Set survival mode |
| `/gma [player]` | `havocsmp.gamemode.adventure` | Set adventure mode |
| `/gmsp [player]` | `havocsmp.gamemode.spectator` | Set spectator mode |

**Note:** Requires `havocsmp.gamemode.others` to change other players' gamemodes

</details>

<details>
<summary><b>🚀 Teleportation Commands</b></summary>

| Command | Aliases | Permission | Description |
|---------|---------|------------|-------------|
| `/tp <player>` | - | `havocsmp.teleport` | Teleport to a player |
| `/tphere <player>` | `/tph` | `havocsmp.teleporthere` | Teleport player to you |
| `/spawn` | - | `havocsmp.spawn` | Teleport to spawn |
| `/setspawn` | - | `havocsmp.setspawn` | Set spawn location |
| `/hub` | - | `havocsmp.hub` | Teleport to hub server |
| `/join <server>` | - | `havocsmp.join` | Connect to specific server |

</details>

<details>
<summary><b>ℹ️ Information Commands</b></summary>

| Command | Permission | Description |
|---------|------------|-------------|
| `/discord` | `havocsmp.discord` | Display Discord invite |
| `/rules` | `havocsmp.rules` | Show server rules |
| `/site` | `havocsmp.site` | Show website link |
| `/store` | `havocsmp.store` | Show store link |
| `/socials` | `havocsmp.socials` | Show social media links |
| `/updates` | `havocsmp.updates` | Show recent updates |
| `/ping [player]` | `havocsmp.ping` | Check connection latency |

</details>

<details>
<summary><b>👤 Player Commands</b></summary>

| Command | Permission | Description |
|---------|------------|-------------|
| `/settings` | `havocsmp.settings` | Open settings GUI |
| `/starter` | `havocsmp.starter` | Claim starter kit (24hr cooldown) |
| `/withdraw <amount>` | `havocsmp.withdraw` | Withdraw hearts (Lifesteal Servers only) |

</details>

---

## 🛠️ Configuration

### config.yml

```yaml
# MySQL Database Configuration
database:
  enabled: true
  host: "localhost"
  port: 3306
  database: "havocsmp"
  username: "root"
  password: "password"
  ssl: false
  pool-size: 10

# Redis Configuration (Cross-Server Support)
redis:
  enabled: true
  host: "localhost"
  port: 6379
  password: ""
  timeout: 2000
  database: 0
  key-prefix: "havocsmp:"

# Spawn Configuration
spawn:
  world: "world"
  x: 0.0
  y: 64.0
  z: 0.0
  yaw: 0.0
  pitch: 0.0

# Hub Configuration
hub:
  enabled: true
  server: "hub"

# Cooldown Configuration (in seconds)
cooldowns:
  starter: 86400  # 24 hours
  spawn: 5
  hub: 5
  message: 3
  teleport: 5

# Feature Configuration
features:
  announcements:
    enabled: true
    interval: 300  # 5 minutes
  join-messages: true
  quit-messages: true
  death-messages: true
```

### messages.yml
All plugin messages are fully customizable with color code support. Includes:
- Command responses & confirmations
- Error messages & warnings
- Success notifications
- Cooldown messages
- Permission denied messages

### announcements.yml
```yaml
announcements:
  - "&6&lHavocSMP &8» &fWelcome to the server!"
  - "&6&lHavocSMP &8» &fVisit our store at &e/store"
  - "&6&lHavocSMP &8» &fJoin our Discord at &e/discord"
  - "&6&lHavocSMP &8» &fType &e/rules &fto view server rules"
```

---

## 🔴 Redis Integration

### Why Redis?
Redis enables **real-time cross-server synchronization**, ensuring a seamless experience across your entire network. Players maintain their status, preferences, and cooldowns regardless of which server they're on.

### Features Using Redis

| Feature | Key Pattern | Description |
|---------|-------------|-------------|
| **Messages** | `havocsmp:messages:disabled:<uuid>` | DM toggle sync |
| **Blocked Players** | `havocsmp:messages:blocked:<uuid>` | Block list sync |
| **Reply Tracking** | `havocsmp:messages:reply:<uuid>` | Last reply target |
| **Cooldowns** | `havocsmp:cooldown:<uuid>:<cmd>` | Shared cooldowns |
| **Command Spy** | `havocsmp:commandspy:<uuid>` | Persistent spy status |
| **Chat Control** | `havocsmp:chat:disabled` | Global chat toggle |

### Redis Pub/Sub Channels
- `havocsmp:alert` - Global alert broadcasting across all servers

### Benefits
- ✅ Instant data synchronization
- ✅ Reduced database load
- ✅ Cross-server cooldowns prevent abuse
- ✅ Network-wide vanish and preferences
- ✅ Real-time global announcements

---

## 📦 Installation

### Quick Setup

1. **Download** the latest `HavocSMPPlugin.jar` from [our website](https://havocsmp.lovable.app/plugins/1)
2. **Place** the JAR in your server's `plugins/` folder
3. **Start** the server to generate configuration files
4. **Configure** database and Redis in `config.yml`
5. **Customize** messages in `messages.yml` and `announcements.yml`
6. **Restart** the server
7. **Done!** 🎉

## 🔧 Dependencies

### Required
- **Spigot/Paper** 1.16 or higher (Tested on 1.21.4)
- **Java** 21+

### Optional
- **[Vault](https://www.spigotmc.org/resources/vault.34315/)** - Required for `/withdraw` command
- **Redis** - Required for cross-server features (highly recommended)

### Built-in
- **[bStats](https://bstats.org/)** - Anonymous metrics collection (automatically included)

---

## 🔨 Building

### Prerequisites
- Java 21 JDK
- Maven 3.6+
- Git

## 🔑 Permissions

### Admin Permissions
- `havocsmp.admin` - Full administrative access
- `havocsmp.*` - All plugin permissions

### Bypass Permissions
- `havocsmp.cooldown.bypass` - Bypass all command cooldowns
- `havocsmp.chat.bypass` - Bypass chat restrictions

### Gamemode Permissions
- `havocsmp.gamemode.creative` - Use creative mode
- `havocsmp.gamemode.survival` - Use survival mode
- `havocsmp.gamemode.adventure` - Use adventure mode
- `havocsmp.gamemode.spectator` - Use spectator mode
- `havocsmp.gamemode.others` - Change others' gamemodes

### Feature Permissions
All other permissions follow the format: `havocsmp.<command>`

---

## 📊 Network Architecture

```
┌─────────────────────────────────────────────┐
│             Redis Server (Central)          │
│  • Cross-server data synchronization       │
│  • Pub/Sub for global alerts               │
│  • Shared cooldowns & preferences          │
└─────────────────────────────────────────────┘
                      ▲
                      │
        ┌─────────────┼─────────────┐
        │             │             │
   ┌────▼───┐    ┌────▼───┐    ┌────▼───┐
   │ Hub    │    │ SMP    │    │ Events │
   │ Server │    │ Server │    │ Server │
   └────────┘    └────────┘    └────────┘
        │             │             │
        └─────────────┼─────────────┘
                      ▼
          ┌───────────────────────┐
          │   MySQL Database      │
          │ (Persistent Storage)  │
          └───────────────────────┘
```

---

## 📊 Statistics & Metrics

This plugin uses bStats to collect anonymous usage statistics. This helps us understand how the plugin is being used and improve it based on real-world data.

**View our stats:** [bStats Plugin Page](https://bstats.org/plugin/bukkit/29429)

### Collected Data
- Server count and player count
- Minecraft version distribution
- Plugin version usage
- Java version statistics

All data is **completely anonymous** and helps improve the plugin. You can opt-out by setting `enabled: false` in `plugins/bStats/config.yml`.

---

## 💬 Support

Need help or have questions?

- 💬 **Discord** - Join our community server

---

## 🙏 Acknowledgments

- Built for the **HavocSMP Network**
- Thanks to all contributors and testers
- Special thanks to the Spigot/Paper community

---

<div align="center">

**⭐ Star this repository if you find it useful!**

**Made with ❤️ for the Minecraft community**

</div>
