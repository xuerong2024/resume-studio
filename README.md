# 简历实验室

无需登录的本地优先简历生成器和投递记录。用户资料保存在各自浏览器的 IndexedDB 中；网站代码托管在 GitHub Pages，不会把简历或投递记录上传到仓库。

项目代码采用 MIT 许可证。`vendor/` 中的 PDF.js 采用 Apache-2.0，Mammoth 采用 BSD-2-Clause；对应许可证文本随库一同分发。

## 第一版功能

- 多份简历，新建、复制、删除；从 TXT、JSON、PDF、DOCX 提取文字后人工整理。
- 岗位 JD、关键词经历匹配、STAR 要点编辑、实时 A4 预览、四边距和密度调整、打印为 PDF。
- 保存岗位简历版本；点击“已投递”记录公司、岗位、时间、所用版本及完整快照。投递记录可更新状态和备注。
- 完整 JSON 备份与恢复。备份含个人信息，请自行保管。
- 不填 API Key 时使用本地 STAR 规则；可复制完整提示词。填写自己的 DeepSeek Key 后尝试调用官方 API，浏览器跨域策略可能阻止直接调用。

## 本地运行

在目录内运行静态 HTTP 服务，例如 `python -m http.server 8000`，然后打开 `http://localhost:8000/`。请不要直接双击 HTML 文件，浏览器对 `file://` 的本地存储及 PDF Worker 支持不一致。

## 发布到 GitHub Pages

1. 新建公开 GitHub 仓库，将本目录的 `index.html`、`styles.css`、`app.js`、`vendor/`、`.github/`、`.gitignore`、`README.md` 上传到 `main` 分支。
2. 仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。
3. 等待 **Deploy GitHub Pages** 工作流完成，打开 Pages 提供的网址。

原有 `%...html` 文件包含个人简历默认资料，已被 `.gitignore` 排除，**请勿手动上传到公开仓库**。发布前也请检查其他文件中是否有个人信息。

## 当前边界

浏览器本地数据不会自动跨设备同步；清除网站数据可能删除资料，请定期备份。岗位搜索目前打开搜索结果供用户核对并粘贴 JD；自动抓取招聘页面需要后端服务。纯 GitHub Pages 也无法安全提供跨域 API 代理；一键云端 AI 的稳定接入需后续部署代理或使用获准的服务。扫描版 PDF 不含可直接提取的文字，需要 OCR 或手动录入。
