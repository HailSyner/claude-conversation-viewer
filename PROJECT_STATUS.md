# Claude 对话记忆查看器 · 当前状态

最后核验：2026-08-12

## 当前版本

- 状态：`complete`
- 源码基线：`main@8b4c1c1`
- 生产入口：<https://non-standard-protocol.space/claude-viewer/>
- 部署形态：Vite 单文件静态应用，由 NSP 生产 Caddy 在独立路径提供。

## 本次部署范围

- 保留 V2 全部现有功能、三套主题、中英文切换、移动端布局以及
  `Made with love by Sylux & Synqa` 署名。
- 不接入 NSP 登录、数据库或后端 API。
- Claude JSON 的读取、解析、搜索、导出与 IndexedDB 缓存均在访问者浏览器本地完成。
- GitHub Pages 不再是唯一可用入口；GitHub 仓库恢复后再补推当前发布记录。

## 验收边界

- `npm run build` 与完整 `npm audit` 通过，生产依赖和开发依赖均为
  `0 vulnerabilities`；发布时使用的单文件 SHA-256 为
  `5e6e08edc8202aacfd1830f7a60abfe2616f6d4ae313d407c5b32c246e16f48f`。
- 本地与公网真实浏览器均通过桌面和 390×844 移动端验收：三套主题、中英文切换、
  最小 Claude JSON 导入、署名、零横向溢出和零 console error。
- 导入含 `<script>` 的测试消息后未生成脚本节点、全局探针保持 `undefined`；公网
  网络请求只有本站 HTML 与浏览器本地 Worker blob，没有对外请求。
- 生产 release `claude-viewer-20260812T112200Z` 已完成 Caddy 配置备份、校验、
  reload 与静态 hash 对账；公网入口、主站、handshake、heartbeat 及既有子域名
  连续性均通过，NSP 后端 PID 和 restart count 未变化。
- GitHub 分支与 PR 因账号暂停暂时无法发布，不影响 NSP 域名上的独立生产部署。
