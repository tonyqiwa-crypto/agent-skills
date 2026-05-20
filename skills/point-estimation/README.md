# Point Estimation

一个用于需求评审、开发计划拆解和 point 估算的 Agent Skill。

适合在拿到需求调研结果、PRD 草稿、会议纪要、流程图之后，快速给出：
- 任务拆分
- 开发计划建议
- 风险与依赖
- 最终标准化 point

## 能力说明

这个 skill 适合处理以下场景：
- 根据需求调研结果评估开发工作量
- 拆分前端、后端、测试、联调等工作项
- 输出版本排期、里程碑、依赖和风险
- 使用统一口径输出总 point

这个 skill 的默认估算方式为“收敛模式”：
- 优先按已有能力复用、配置改造、最小必要改动来估算
- 不因为上下文缺失就自动上浮一档
- 除非明确要求，否则不按保守模式估算

## 估点规则

### 任务级 point

任务级估点使用以下口径：
- `1`：微小改动，影响单一模块，规则简单，风险低
- `2`：小型改动，存在少量联调或边界处理
- `3`：标准需求项，需要跨 1-2 个模块协作
- `5`：中等复杂度，规则较多，联调和回归成本明显
- `8`：高复杂度，跨多个系统，有较多不确定性或兼容成本
- `13`：超大项，建议继续拆分

### 最终总 point

最终总 point 只输出以下标准值：
- `1`
- `2`
- `3`
- `5`
- `8`
- `13`

当前采用“就低不就高”的归一化规则：
- 原始汇总 `<= 1`，最终总 point 为 `1`
- 原始汇总 `> 1` 且 `<= 2`，最终总 point 为 `1`
- 原始汇总 `> 2` 且 `<= 3`，最终总 point 为 `2`
- 原始汇总 `> 3` 且 `<= 5`，最终总 point 为 `3`
- 原始汇总 `> 5` 且 `<= 8`，最终总 point 为 `5`
- 原始汇总 `> 8` 且 `<= 13`，最终总 point 为 `8`
- 原始汇总 `> 13`，最终总 point 为 `13`

## 安装方式

### 方式一：直接随项目使用

如果你是项目成员，直接把以下目录提交到仓库即可：

```text
.trae/skills/point-estimation/
  ├── SKILL.md
  └── README.md
```

其他人拉取代码后，就可以在该项目内使用这个 skill。

### 方式二：做成独立仓库供别人安装

建议仓库结构如下：

```text
your-skill-repo/
  └── skills/
      └── point-estimation/
          ├── SKILL.md
          └── README.md
```

发布到 GitHub 或 GitLab 后，别人可以通过 Skills CLI 安装：

```bash
npx skills add <你的仓库地址> --skill point-estimation
```

如果仓库里只有这一个 skill，也可以直接安装整个仓库：

```bash
npx skills add <你的仓库地址>
```

## 使用方式

安装后，可以直接让 Agent 调用这个 skill 来估算需求。

示例提示词：

```text
根据以下需求调研结果，调用 point-estimation skill，进行 point 评估：

1. 商品质检中，未提交质检结果，商品编码扫描输入框置灰不可编辑
2. 商品质检中，取消质检按钮恢复展示，可点击按钮取消质检
3. 订单存在质检中商品，运单号扫描输入框置灰不可编辑
```

也可以这样用：

```text
请按 point-estimation skill 的规则评估下面需求，并输出任务拆分、风险和最终总 point。
```

## 输出内容

这个 skill 默认输出以下结构：
- 需求理解与假设
- 任务拆分与任务级 point
- 原始汇总 point
- 最终总 point
- 开发计划建议
- 风险、依赖和待确认问题

## 适用建议

适合：
- 需求初评
- 版本排期前的快速估算
- 多个需求之间的相对工作量比较
- 团队统一估点口径

不适合：
- 直接替代详细技术方案评审
- 在完全没有上下文时作为最终开发承诺
- 需要精确到人天且涉及多人并行排班的正式排期

## 文件位置

当前项目内 skill 文件位置：
- [SKILL.md](file:///Users/cupshe/Desktop/cs-wms-pda-printer/.trae/skills/point-estimation/SKILL.md)
- [README.md](file:///Users/cupshe/Desktop/cs-wms-pda-printer/.trae/skills/point-estimation/README.md)
