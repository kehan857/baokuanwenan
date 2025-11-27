# 爆款文案生成 - AI智能助手

基于 Coze 智能体 SDK 的爆款文案生成工具，支持无需登录即可使用。

## 项目简介

这是一个单页面 Web 应用，集成了 Coze 智能体的 Chat SDK，为用户提供 AI 驱动的文案生成服务。通过服务访问令牌（SAT）实现无需用户登录即可访问。

## 功能特性

- 🤖 AI 智能文案生成
- 🔒 无需登录即可使用
- 📱 响应式设计，支持移动端和桌面端
- 🎨 现代化的 UI 设计
- ⚡ 快速加载和响应

## 技术栈

- HTML5
- CSS3
- Coze Web SDK (1.2.0-beta.19)

## 部署到 GitHub Pages

### 方法一：通过 GitHub 网页界面

1. 将代码推送到 GitHub 仓库：
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Coze SDK integration"
   git branch -M main
   git remote add origin https://github.com/kehan857/baokuanwenan.git
   git push -u origin main
   ```

2. 在 GitHub 仓库中启用 Pages：
   - 进入仓库的 `Settings` 页面
   - 找到 `Pages` 选项
   - 在 `Source` 部分选择 `Deploy from a branch`
   - 选择 `main` 分支和 `/ (root)` 目录
   - 点击 `Save`

3. 等待几分钟后，访问 `https://kehan857.github.io/baokuanwenan/` 即可查看部署的页面

### 方法二：使用 GitHub Actions（可选）

如果需要自动部署，可以创建 `.github/workflows/deploy.yml` 文件（本项目已包含基础结构，可根据需要扩展）。

## 本地开发

1. 克隆仓库：
   ```bash
   git clone https://github.com/kehan857/baokuanwenan.git
   cd baokuanwenan
   ```

2. 使用本地服务器运行：
   ```bash
   # 使用 Python
   python -m http.server 8000
   
   # 或使用 Node.js
   npx serve .
   
   # 或使用 PHP
   php -S localhost:8000
   ```

3. 在浏览器中访问 `http://localhost:8000`

## 配置说明

### SDK 配置

项目使用以下配置：

- **App ID**: `7576948828981608511`
- **Workflow ID**: `7577062163073941540`
- **认证方式**: 服务访问令牌（SAT）

### 修改配置

如需修改配置，请编辑 `index.html` 文件中的以下部分：

```javascript
"appInfo": {
    "appId": "你的AppID",
    "workflowId": "你的WorkflowID"
},
"auth": {
    "type": "token",
    "token": "你的SAT令牌",
    onRefreshToken: function () {
        return "你的SAT令牌";
    }
}
```

## 文件结构

```
/
├── index.html          # 主页面文件
├── styles.css          # 样式文件
├── .gitignore         # Git 忽略文件
├── README.md          # 项目文档
└── .github/           # GitHub 配置文件（可选）
```

## 注意事项

1. **安全性**: 服务访问令牌（SAT）已直接嵌入在 HTML 中。虽然 GitHub Pages 是公开的，但请注意保护您的令牌安全。如果令牌泄露，请及时在 Coze 平台重新生成。

2. **浏览器兼容性**: 建议使用现代浏览器（Chrome、Firefox、Safari、Edge 最新版本）。

3. **网络要求**: 需要能够访问 Coze CDN (`lf-cdn.coze.cn`)。

## 故障排除

### 403 Forbidden 错误

如果遇到 403 错误，可能的原因和解决方案：

#### 1. SAT 令牌权限问题

**检查步骤：**
- 登录 Coze 开放平台
- 进入"服务访问令牌"管理页面
- 确认 SAT 令牌：
  - 是否仍然有效（未过期）
  - 是否有访问目标 App 的权限
  - 是否与 App ID `7576948828981608511` 正确关联

**解决方案：**
- 如果令牌无效或权限不足，请在 Coze 平台重新生成 SAT 令牌
- 确保新令牌有完整的 API 访问权限
- 更新 `index.html` 中的令牌

#### 2. CORS 配置

根据 Coze API 的 CORS 策略：
- `Access-Control-Allow-Origin: *`（允许所有域名）
- `Access-Control-Allow-Credentials: false`（禁止凭据）

**注意事项：**
- 确保请求不携带不必要的凭据（如 Cookies）
- 令牌应通过 `Authorization: Bearer <token>` 头传递
- 当前配置已符合要求，无需额外调整

#### 3. App 和 Workflow 配置

**检查步骤：**
- 确认 App ID `7576948828981608511` 是否正确
- 确认 Workflow ID `7577062163073941540` 是否正确
- 确认 App 已发布且可访问
- 确认 App 允许通过 SAT 令牌访问

#### 4. 查看详细错误信息

如果问题仍然存在：
- 打开浏览器开发者工具（F12）
- 查看 Network 标签中的请求详情
- 检查响应头中的 `x-tt-logid`，可用于联系 Coze 技术支持查询具体错误原因

### 其他常见问题

#### 页面无法加载
- 检查 GitHub Pages 是否已正确部署
- 清除浏览器缓存或使用无痕模式
- 确认访问的 URL 正确：`https://kehan857.github.io/baokuanwenan/`

#### SDK 加载失败
- 检查网络连接，确保能访问 `lf-cdn.coze.cn`
- 检查浏览器控制台是否有错误信息
- 尝试刷新页面

## 参考文档

- [Coze Web SDK 安装指南](https://www.coze.cn/open/docs/developer_guides/install_web_sdk)
- [Coze 身份验证文档](https://www.coze.cn/open/docs/developer_guides/authentication)

## 许可证

本项目仅供学习和参考使用。

## 更新日志

### v1.0.0 (2025-01-XX)
- 初始版本
- 集成 Coze Web SDK
- 实现 SAT 认证
- 响应式设计

