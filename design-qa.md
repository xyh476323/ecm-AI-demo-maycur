# Design QA：全屏快速切换对话

- source visual truth path: `/var/folders/yk/m7mdj7lj5391fsv16bv7qd4h0000gn/T/codex-clipboard-cb3fd93b-ba58-41e6-b7f8-b974864ce180.png`
- implementation screenshot path: `/Users/xyh/.codex/visualizations/2026/07/10/019f4b61-28f0-7433-959d-aca5a0a8d087/history-quick-preview-final.png`
- full-view comparison evidence: `/Users/xyh/.codex/visualizations/2026/07/10/019f4b61-28f0-7433-959d-aca5a0a8d087/history-quick-preview-comparison-final.png`
- focused region comparison evidence: `/Users/xyh/.codex/visualizations/2026/07/10/019f4b61-28f0-7433-959d-aca5a0a8d087/history-quick-preview-focused-comparison-final.png`
- viewport: `1280 × 720`
- state: AI 应用中心全屏模式、历史侧栏收起、快速历史浮层展开

## Findings

- 未发现 P0/P1/P2 问题。
- 字体与排版：浮层会话使用 PingFang SC 14px/20px，分区标题使用 12px/20px；修正后字号、字重、截断方式与设计稿一致。
- 间距与布局：浮层宽 250px、高 264px，距展开按钮 4px；12px 内边距、34px 行高、14px 分区间距与设计稿的密度和节奏一致。
- 色彩与视觉 token：白色浮层、`rgba(0,0,0,.28)` 分区标题、深色会话文字、`#f0f0f2` hover 背景及克制阴影均沿用现有 Maycur AI 组件。
- 图片与图标：复用项目现有 `sidebar-toggle.svg`、`new-group.svg`、`pin-badge.svg`，未使用占位图标或临时绘制资产。
- 文案与内容：分组名称与当前项目一致，最近对话读取当前历史数据并限制为 3 条；设计稿中的“测试”属于示例数据，本地实现保留当前真实预设记录。

## Interaction Verification

- hover/focus 打开浮层，离开后收起。
- 点击最近对话可切换至对应会话结果。
- 点击分组可展开完整历史栏，并保持分组区域展开。
- 点击展开按钮仍可直接打开完整历史栏。
- 触发按钮不再同时显示 tooltip，避免与浮层重叠。
- 键盘焦点可打开浮层并进入浮层内容。
- 页面控制台错误：0。

## Comparison History

### Iteration 1

- Earlier finding: 会话文字为 13px 且颜色偏浅，和设计稿相比层级不足（P2）。
- Fix: 调整为 14px/20px、`rgba(0,0,0,.85)`。
- Post-fix evidence: `history-quick-preview-focused-comparison-final.png`，字体、行高、截断和内容密度已对齐。

## Open Questions

- 无。

## Implementation Checklist

- [x] 全屏模式 hover 展开快速历史浮层
- [x] 展示 2 个分组与最近 3 条对话
- [x] 保留省略号与完整文案 tooltip
- [x] 保留置顶状态
- [x] 支持直接切换对话与展开完整侧栏
- [x] 窄屏宽度保护与浮层最大高度滚动
- [x] 键盘可达性和控制台检查

## Follow-up Polish

- P3：设计稿使用示例文案“测试”，本地演示使用当前预设历史记录；属于数据差异，不影响组件还原。

final result: passed
