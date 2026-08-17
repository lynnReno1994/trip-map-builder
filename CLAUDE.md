# trip-map-builder - 旅行地图技能包
Markdown + HTML + OpenCLI references

<directory>
assets/ - 单文件地图模板 (1文件: template.html)
skills/ - 三阶段子技能 (plan.md, research.md, build.md)
references/ - 调研与规划方法论 (trip-planning.md, dianping-research.md, xhs-research.md)
references/cache/ - 本地餐厅/景点缓存，按城市存档，调研前优先查询
</directory>

<config>
README.md - 对外说明技能定位、安装、流程和目录结构
SKILL.md - Agent 技能入口，路由到 skills/ 子技能，包含共享记忆配置
</config>

法则: 行程是参考坐标，不是执行脚本。记忆只存下次仍有用的偏好。餐厅先看当天区域，再看大众点评和小红书。

[PROTOCOL]: 变更时更新此头部，然后检查 CLAUDE.md
