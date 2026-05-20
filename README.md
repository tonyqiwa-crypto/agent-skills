# agent-skills

一个用于存放和分享 Agent Skills 的仓库。

当前已包含的 skill：
- `point-estimation`：用于需求评审、开发计划拆解和 point 估算

## 已收录 Skills

### point-estimation

适合以下场景：
- 根据需求调研结果评估开发工作量
- 拆分前端、后端、测试、联调等工作项
- 输出版本排期、里程碑、依赖和风险
- 使用统一口径输出最终总 point

Skill 目录：
- `skills/point-estimation/`

文件：
- `skills/point-estimation/SKILL.md`
- `skills/point-estimation/README.md`

## 安装方式

安装 `point-estimation`：

```bash
npx skills add https://github.com/tonyqiwa-crypto/agent-skills --skill point-estimation
```

如果以后仓库里有多个 skill，也可以继续按 `--skill <name>` 的方式选择安装。

## 使用示例

```text
请调用 point-estimation skill，评估以下需求的开发 point：

1. 商品质检中，未提交质检结果，商品编码扫描输入框置灰不可编辑
2. 商品质检中，取消质检按钮恢复展示，可点击按钮取消质检
3. 订单存在质检中商品，运单号扫描输入框置灰不可编辑
```

## 仓库结构

```text
agent-skills/
  └── skills/
      └── point-estimation/
          ├── SKILL.md
          └── README.md
```

## 说明

- `SKILL.md`：skill 的核心规则与触发条件
- `README.md`：该 skill 的安装和使用说明
- 当前 `point-estimation` 默认采用“收敛模式”估算
- 最终总 point 使用标准化口径输出：`1 / 2 / 3 / 5 / 8 / 13`
