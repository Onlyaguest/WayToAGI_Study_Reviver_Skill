# 🧠 WayToAGI Study Reviver Skill

> 让 Agent 通过 3-4 轮轻松互动，理解用户学习目标和基础水平，再从飞书知识库精准推荐学习路径并自动生成飞书文档。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 它解决什么问题

很多“学习路径推荐”都太模板化：

- 不先了解用户基础，推荐内容过难或过浅
- 给一堆链接但没有阶段顺序
- 不落地成文档，回头难复用

这个 Skill 的目标是：**先聊清楚，再精准搜索，最后交付可执行的学习路径文档。**

## 它怎么工作

```
用户说“我想学XX”
      │
      ▼
互动问答（3-4轮）
(目标 / 基础 / 时间 / 风格)
      │
      ▼
docs +search 搜索知识库
(必须搜索，不遍历)
      │
      ▼
学习路径分阶段组织
(入门 → 进阶 → 实战)
      │
      ▼
docs +create 生成飞书文档
```

没有后端服务，没有数据库。**lark-cli + SKILL.md = 全流程。**

## 快速开始

### 前置条件

```bash
# 安装 lark-cli（参考官方文档）
# https://github.com/larksuite/cli

# 登录并授权（至少 docs，建议 docs/base/im/wiki）
lark-cli auth login --domain docs,base,im,wiki
```

### 用法

把 `SKILL.md` 提供给你的 Agent（Codex / Claude Desktop / Cursor 等），然后对 Agent 说：

```plaintext
我想学 AI 基础入门
```

Agent 会自动按 Skill 流程执行：

1. 先问你 3-4 轮问题
2. 根据你的回答生成搜索关键词
3. 搜索飞书知识库并筛选文章
4. 生成结构化学习路径
5. 创建飞书文档交付

## Skill 能力

| 能力 | 说明 | 输出 |
|------|------|------|
| 互动画像识别 | 通过轻量问答识别学习目标和基础 | 用户学习画像 |
| 知识库精准搜索 | 基于画像动态生成关键词并搜索 | 搜索结果集合 |
| 学习路径生成 | 按难度与时间组织阅读顺序 | 路径清单（含原始 URL） |
| 文档交付 | 自动写入飞书文档 | 可分享学习路径文档 |

## Use Cases

### 1. 新手 AI 入门

```plaintext
我完全是小白，想学 AI 基础入门。
```

输出：低门槛、短时长、先概念后实践的 2-3 周学习路径。

### 2. 有编程基础想转 Agent

```plaintext
我会 Python，想系统学多智能体架构。
```

输出：从 Agent 核心组件到多智能体模式再到实战文章的进阶路径。

### 3. 时间很少的职场学习

```plaintext
我每周只能投入 2 小时，给我最短路径。
```

输出：精简版“必读 3-5 篇”，并标注阅读顺序与预估时间。

## 设计原则

- 先聊再搜：不做“上来就搜”
- 只推原文：不改写知识库内容，不搬运
- 可复用交付：最终必须产出飞书文档
- 轻交互：问题不超过 4 轮，像聊天不是填问卷

## 文件结构

```
├── SKILL.md          # Skill 定义（Agent 执行核心）
├── README.md         # 人类使用说明
└── LICENSE
```

## 版本说明

- 当前发布内容以 `SKILL.md` 头部 metadata 为准（`name` / `version`）
- 本仓库保持最小发布形态，仅保留 Skill 必要文件

## License

MIT
