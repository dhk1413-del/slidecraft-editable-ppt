# SlideCraft 图片转可编辑 PPT

`slidecraft-editable-ppt` 是面向 SlideCraft 工作台的图片、PDF 和图片版 PPT/PPTX 重建 Skill。它用 `editppt` CLI 管理逐页准备、重建、校验与合成；文字、表格和简单结构会尽量生成 PowerPoint 原生对象，照片、复杂图形和公式可能保留为图片。

## 安装

把 `skills/slidecraft-editable-ppt/` 安装到代理的 Skill 目录，并在 Python 3.10+ 环境中安装命令行工具：

```bash
pipx install --force --editable skills/slidecraft-editable-ppt/cli
editppt doctor
```

使用 `$slidecraft-editable-ppt` 调用 Skill。底层命令保持 `editppt`，现有 run/manifest 格式和命令接口保持兼容。此仓库是独立改造版；把它接入现有 SlideCraft 服务，需要另行更新服务的 Skill 路径和 worker 配置。

## 数据与凭据

- `OPENAI_API_KEY` 与 `PADDLE_OCR_TOKEN` 只从私有进程环境读取；不要写入仓库、提示词、run 目录或 `~/.editppt/config.yaml`。
- 仅在用户允许外部处理时发送任务所需页面与提示词。没有外部 OCR 时可使用本地文字提示；关键文字仍无法辨认时应报告失败。
- Codex OAuth 图像请求固定使用官方端点。

原项目：[`ningzimu/image-to-editable-ppt-skill`](https://github.com/ningzimu/image-to-editable-ppt-skill)。本改造版保留原项目的 MIT 许可与署名，见 [LICENSE](LICENSE)。
