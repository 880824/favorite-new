# 🐌 蜗牛个人导航 (CloudNav)

一个现代化的云端导航页面，帮助您管理和快速访问常用网站链接。

## ✨ 功能特性

- **🔗 书签管理**：添加、编辑、删除网站链接，支持图标、描述等自定义信息
- **📂 分类管理**：无限层级分类目录，支持密码保护子分类
- **🔍 智能搜索**：站内搜索 + 外部多搜索引擎集成
- **📌 置顶功能**：灵活拖拽排序，快速访问高频网站
- **🌓 深色模式**：自动跟随系统主题，支持手动切换
- **📱 响应式设计**：完美适配桌面端和移动端
- **🔐 安全认证**：管理员密码保护，敏感操作需验证
- **🤖 AI 集成**：支持 Google Gemini、OpenAI 兼容、Claude 等 AI 服务
- **💾 数据导入导出**：Chrome 书签 HTML / JSON 备份格式
- **☁️ 云端同步**：数据存储在 Cloudflare KV，多设备自动同步
- **🌐 浏览器扩展支持**：提供 REST API 供 Chrome 扩展等外部调用

## 🚀 部署（Cloudflare Pages）

### 一键部署

1. Fork 本仓库或直接将文件上传到 GitHub
2. 在 Cloudflare 控制台创建 Pages 项目
3. **框架预设**：选择 **无**
4. **构建命令**：留空
5. **输出目录**：留空
6. 绑定 KV 命名空间：
   - 在 Cloudflare 控制台创建一个 KV 命名空间
   - 在 Pages 项目的「设置 → 绑定」中添加 KV 绑定
   - **变量名称**：`CLOUDNAV_KV`
7. 添加环境变量：
   - `PASSWORD`：管理员登录密码
8. 部署完成！✅

> **说明**：本项目为预构建的静态站点，无需任何构建步骤，Cloudflare Pages 直接托管即可。

## 📁 项目结构

```
.
├── assets/                    # 静态资源（JS/CSS 打包文件）
├── functions/api/             # Cloudflare Pages Functions（后端 API）
│   ├── _kvAdapter.js          # KV 存储适配器
│   ├── auth.js                # 认证接口
│   ├── debug.js               # 调试接口
│   ├── link.js                # 链接接口（API 添加）
│   └── storage.js             # 统一存储接口
├── index.html                 # 入口页面
├── _routes.json               # Cloudflare 路由配置
└── ...
```

## 📝 环境变量

| 变量名 | 必需 | 说明 |
|--------|------|------|
| `PASSWORD` | 是 | 管理员登录密码 |
| `ALLOWED_ORIGIN` | 否 | CORS 允许的来源，默认 `*` |

## 🔧 Cloudflare KV 绑定

在 Cloudflare Pages 控制台添加 KV 命名空间绑定：

- **绑定名称**：`CLOUDNAV_KV`
- **用途**：存储所有用户数据（链接、分类、配置等）

## 📄 许可

MIT License