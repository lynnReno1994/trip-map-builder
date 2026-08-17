---
name: trip-map-builder
description: >
  End-to-end trip planning: gather user constraints, build a reference
  itinerary, research locations and dining signals via 大众点评 + 小红书, then
  generate an interactive mobile-first map page (Leaflet + timeline) and
  optionally deploy to Vercel. Use when user asks to plan a trip, create an
  itinerary, research restaurants on 大众点评/小红书, build a trip map page, or
  says "行程规划", "行程地图", "trip map", "plan my trip", "做个行程". Covers the full
  pipeline from scattered inputs (screenshots, wishlists) to a deployable
  reference map with navigation links, 小红书 links, payment info, and
  reservation buttons.
---

# Trip Map Builder

Three-phase pipeline: **Plan → Research → Build**.

The output is a **reference itinerary**, not a script the traveler must obey.
During the trip, weather, current location, fatigue, and hunger can override
the original plan.

## Phase routing

| User intent | Load |
|---|---|
| 排行程 / plan itinerary | `skills/plan.md` |
| 查餐厅 / research dining | `skills/research.md` |
| 生成地图 / build map | `skills/build.md` |
| 全流程 from scratch | All three, in order |

When in doubt, run all three phases sequentially.

## Shared memory

### 读哪里

按以下优先级选一个，不要同时写两处：

1. **Claude Code 环境**（项目目录下有 `.claude/` 且 auto memory 可用）：
   使用 auto memory 系统（`~/.claude/projects/<hash>/memory/`）。
   写旅行偏好时用 `type: user` 或 `type: project` 的独立 `.md` 文件，遵循 auto memory 格式。

2. **其他环境**（Cursor、其他 IDE、命令行）：
   使用 `~/.trip-map-builder/MEMORY.md`。文件不存在时继续，不要阻塞。

Before planning or building, load memory from whichever path above applies.
Use it only for durable traveler context:

- pace preference
- food and drink preferences
- budget habits
- payment and navigation preferences
- previously generated trip outputs
- recurring constraints and unresolved follow-ups

Do not store raw screenshots, passport data, booking codes, full chat logs, or
other sensitive/private material.

After each completed trip plan, research pass, or map build, write back durable
facts to the active memory path. For `~/.trip-map-builder/MEMORY.md`, use this
template:

```md
# Trip Map Builder Memory

## Traveler Defaults
- Departure city:
- Pace:
- Food preferences:
- Budget habits:
- Payment preference:
- Navigation preference:
- Language preference:

## Past Trips
| Trip | Dates | Destination | Output | Notes |
|------|-------|-------------|--------|-------|

## Reusable Preferences
-

## Open Threads
-
```

## Dependencies

| Tool | Purpose | Install |
|------|---------|---------|
| [OpenCLI](https://github.com/jackwener/OpenCLI) | 大众点评 adapter + 小红书调研 | `npm install -g @jackwener/opencli` |
| Chrome/Chromium | 浏览器 + 远程调试 | 已有 |
| [Leaflet.js](https://leafletjs.com) | 地图渲染（CDN 引入，无需安装） | template.html 内置 |
| [gh CLI](https://cli.github.com) | GitHub 仓库创建（可选） | `brew install gh` |

## Resources

- `skills/plan.md` — Phase 1 行程规划指令
- `skills/research.md` — Phase 2 调研指令（含缓存查找逻辑）
- `skills/build.md` — Phase 3 地图生成指令
- `references/trip-planning.md` — 行程规划方法论
- `references/dianping-research.md` — 大众点评 OpenCLI 工作流
- `references/xhs-research.md` — 小红书 CDP 工作流
- `references/cache/` — 本地餐厅 / 景点缓存（按城市）
- `assets/template.html` — 地图模板（Leaflet + Apple design system）
- [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) — 60+ brand design systems
