# godot-agent-skills

一套面向 AI Agent 的 Godot 4.x 技能包（Agent Skills 格式），覆盖从写代码、搭 UI、做优化到 AI 生成美术资源的完整链路。

## 包含的技能

| 技能 | 定位 | 触发场景 |
|---|---|---|
| `godot-development` | Godot 引擎总纲：场景、节点、GDScript、项目结构 | 处理 .tscn / .gd 文件、搭建项目骨架、解决引擎相关问题 |
| `godot-best-practices` | Godot 4.x 编码最佳实践 | 场景组织、信号、资源、状态机、项目结构决策 |
| `godot-gdscript-patterns` | GDScript 设计模式与惯用法 | 信号、场景实例化、状态机、性能写法 |
| `godot-ui` | Control 节点 / 主题 / 响应式布局 | 菜单、HUD、背包、设置界面等 UI 实现 |
| `godot-optimization` | 性能剖析与优化 | 定位瓶颈、draw call、内存、脚本优化 |
| `godot-asset-generator` | AI 美术资源生成流水线 | 文生图→去背→精灵图打包→生成 .import 配置 |

## 目录结构

```
skills/
├── godot-development/
├── godot-best-practices/
│   ├── assets/templates/        # autoload-manager / base-script / state-machine 模板
│   └── references/              # 架构、GDScript、设计模式参考
├── godot-gdscript-patterns/
│   └── references/advanced-patterns.md
├── godot-ui/
├── godot-optimization/
└── godot-asset-generator/
    ├── assets/prompts/          # 像素画提示词模板
    ├── assets/style-guides/
    ├── references/              # DALL·E API、导入设置、提示词指南
    └── scripts/                 # 生成 / 批处理 / 后处理 / 打包脚本
```

## 安装

把 `skills/` 下需要的目录复制到你的 Agent 技能目录即可：

```bash
# WorkBuddy / Claude Code 用户级
cp -r skills/* ~/.workbuddy/skills/

# 或项目级
cp -r skills/* .workbuddy/skills/
```

复制后重启会话（或重新加载技能列表）即生效，无需额外配置。

## 依赖与前提

- 除 `godot-asset-generator` 外，其余技能均为纯知识型，无运行时依赖。
- `godot-development` 声明了 `mcp__godot__*`，配合 Godot MCP 服务端可读写真实项目；没有 MCP 时仍可作为知识参考使用。
- `godot-asset-generator` 需要：
  - [Deno](https://deno.com/) 运行时（脚本为 TypeScript）
  - 至少一个图像生成服务的 API Key：`OPENAI_API_KEY` / `REPLICATE_API_TOKEN` / `FAL_KEY`

## License

MIT（源自各技能包 frontmatter 声明）。
