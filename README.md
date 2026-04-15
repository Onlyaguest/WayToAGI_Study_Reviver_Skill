# WayToAGI Study Reviver Skill

`lark-study-reviver` 的稳定发布仓库（仅保留技能定义与说明）。

## 包含内容

- `SKILL.md`：可直接被 Agent 读取执行的 Skill 定义
- `README.md`：使用说明与定位说明
- `LICENSE`

不包含 Demo 应用、数据目录或前端代码，保持最小可复用分发形态。

## Skill 简介

这个 skill 用于：

1. 通过 3-4 轮轻量互动问答识别用户学习目标与基础
2. 基于用户画像生成关键词并搜索飞书知识库（`lark-cli docs +search`）
3. 输出带原始链接的分阶段学习路径
4. 创建飞书文档保存完整学习路线

核心原则：先聊再搜，搜完就推；不搬运、不改写原文。

## 使用前置

- 已安装 `lark-cli`
- 已完成登录与授权（至少包含 docs 域）

建议授权命令：

```bash
lark-cli auth login --domain docs,base,im,wiki
```

## 触发方式

当用户表达类似意图时使用：

- “我想学 AI 基础入门”
- “我想学 Agent”
- “给我做一个学习路径”

## 版本

当前版本以 `SKILL.md` 头部 metadata 为准。
