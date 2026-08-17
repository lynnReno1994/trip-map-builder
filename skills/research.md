# Phase 2: Research

Read `references/dianping-research.md` for 大众点评 workflow.
Read `references/xhs-research.md` for 小红书 CDP workflow.

## Cache-first lookup (新增)

在调用 OpenCLI 之前，先查本地缓存：

```
references/cache/{city}.md
```

命中条件：城市匹配 **且** 区域匹配 **且** 缓存日期在 **90 天内**。

| 场景 | 处理 |
|---|---|
| 完全命中 | 直接引用缓存数据，跳过 OpenCLI 调用 |
| 部分命中 | 命中的区域用缓存，缺失的区域走 OpenCLI |
| 未命中 / 过期 | 全量走 OpenCLI，调研完成后写回缓存 |

缓存写回格式见 `references/cache/README.md`。

## Research sequence

1. 按 Phase 1 输出的每日区域逐一调研
2. 每个区域：大众点评搜餐厅 → 看详情 → 小红书补氛围
3. 每餐只保留 2-3 个候选，格式见 `references/dianping-research.md` § 写回格式

## Filtering rules

大众点评（硬信号）：口味、排队风险、价格、是否在当天区域内  
小红书（软信号）：氛围、近期体验、拍照价值、软性提醒

- Keep: 具体店名、地址、菜品、个人体验、重复关键词
- Drop: 泛区域盘点、转发、纯情绪、"氛围很好" × 3

## Output

每个餐位：主推候选 + 近距离备选，各含大众点评判断 + 小红书补充。
手交 Phase 3，附结构化地点数据（name, lat/lng, type, time, desc）。
