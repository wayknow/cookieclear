# CookieClear — 隐私优先的浏览器 Cookie 编辑器

> Chrome 扩展（MV3），MIT 开源。MVP 完成，等待 CWS 开发者审核。

## 项目概览

- **技术栈**：Vanilla JS + ES modules，零框架依赖，CSS 变量驱动主题
- **测试**：`npm test`（76 个测试，Puppeteer e2e + Node 原生模块）
- **当前状态**：MVP 完成，CWS 商店素材已备好，等待开发者身份审核
- **详细状态**：[STATUS.md](STATUS.md)
- **产品规格**：[PRODUCT.md](PRODUCT.md)

## 关键架构

- popup 通过 `<script type="module" src="popup.js">` 加载，ES module `import` 解析依赖
- 模块关系：`popup.js → cookies.js / classify.js / export.js / import.js / storage.js / undo.js`
- `classify.js` 内嵌 Disconnect.me 追踪器域名列表（101 条），通过 `chrome.runtime.getURL()` 加载
- Cookie 分类：name 正则匹配 → domain 匹配追踪器列表 → 隐私评分 0-100
- 撤销栈：内存中维护（popup 会话内有效），最大 50 条
- 域名白名单：`chrome.storage.local` 持久化，批量删除时跳过
- 定价：**完全免费**，无 Pro 层级，作为 ClearJSON/SnapMark 的获客入口
- 竞品定位：替代被 CWS 移除的 EditThisCookie（300 万用户），免费、开源、零追踪
- 不做：Pro 付费、订阅、广告、数据收集、云端同步、用户账号

## 本地测试

- 在 Chrome `chrome://extensions` 中「加载已解压的扩展程序」，选择项目根目录
- 打开任意网站（如 github.com），点击 toolbar 中 CookieClear 图标即可测试 popup
- 截图工具：`node -e "..."` 见 `store-assets/` 下的生成脚本
- 商店素材：`store-assets/CWS_STORE.md`（描述 + SEO 关键词）+ 2 张截图

## 工作约定

- 改动功能或修复问题后更新 PRODUCT.md / STATUS.md 同步状态
- 提交前跑 `npm test`，76 个测试必须全部通过
- 提交信息包含改动说明 + `Co-Authored-By: Claude <noreply@anthropic.com>`
- 推送到 `git@github.com:wayknow/cookieclear.git`，分支 `main`
- 上下文快满时说"做检查点"：更新文档 → git commit → 提示清空重启
