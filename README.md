# 智光 (Zhiguang) 前端

一个基于 React + TypeScript 构建的知识分享社区平台前端应用。

## 技术栈

- **框架**: React 18 + TypeScript
- **构建工具**: Vite 5
- **路由**: React Router v6
- **样式**: CSS Modules + CSS Variables
- **AI集成**: @coze/api
- **Markdown渲染**: react-markdown + remark-gfm

## 功能模块

### 认证系统
- 手机/邮箱/用户名多种方式登录
- 验证码登录与密码登录
- 用户注册与验证码验证
- JWT Token 认证与自动刷新

### 知文 (KnowPost)
- 图文内容创作与发布
- Markdown 内容编辑
- 内容点赞与收藏
- Feed 流浏览
- 内容可见性控制（公开/粉丝可见/仅自己可见等）

### 用户关系
- 关注/取消关注用户
- 粉丝与关注列表查看
- 用户资料展示与编辑
- 头像上传

### 搜索功能
- 内容全文搜索
- 搜索建议与自动补全
- 标签筛选

## 项目结构

```
src/
├── components/          # 组件目录
│   ├── cards/          # 卡片组件
│   ├── common/         # 通用组件（按钮、标签、搜索框等）
│   ├── icons/          # 图标组件
│   └── layout/         # 布局组件（侧边栏、头部等）
├── context/            # React Context
│   └── AuthContext.tsx # 认证上下文
├── features/           # 功能模块
│   └── auth/          # 认证相关功能
├── pages/              # 页面组件
│   ├── HomePage.tsx           # 首页
│   ├── SearchPage.tsx         # 搜索页
│   ├── CreatePage.tsx         # 创建内容页
│   ├── LearningPage.tsx       # 学习页
│   ├── ProfilePage.tsx        # 个人主页
│   ├── EditProfilePage.tsx    # 编辑资料页
│   ├── CourseDetailPage.tsx   # 内容详情页
│   ├── LoginPage.tsx          # 登录页
│   └── RegisterPage.tsx       # 注册页
├── services/           # API 服务层
│   ├── apiClient.ts    # HTTP 客户端封装
│   ├── authService.ts  # 认证服务
│   ├── knowpostService.ts # 知文服务
│   ├── profileService.ts  # 用户资料服务
│   ├── relationService.ts # 用户关系服务
│   └── searchService.ts   # 搜索服务
├── theme/              # 主题配置
├── types/              # TypeScript 类型定义
├── App.tsx             # 应用入口组件
├── main.tsx            # 应用启动入口
└── index.css           # 全局样式
```

## 页面路由

| 路由 | 页面 | 说明 |
|------|------|------|
| `/` | HomePage | 首页，展示知文 Feed 流 |
| `/search` | SearchPage | 搜索页面 |
| `/create` | CreatePage | 创建知文内容 |
| `/learn` | LearningPage | 学习页面 |
| `/profile` | ProfilePage | 个人主页 |
| `/profile/edit` | EditProfilePage | 编辑个人资料 |
| `/post/:id` | CourseDetailPage | 知文详情页 |
| `/login` | LoginPage | 登录页 |
| `/register` | RegisterPage | 注册页 |

## 快速开始

### 环境要求

- Node.js >= 18.0.0
- npm >= 9.0.0

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
npm run dev
```

应用将在 http://localhost:5173 启动。

### 构建生产版本

```bash
npm run build
```

### 预览生产版本

```bash
npm run preview
```

### 类型检查

```bash
npm run lint
```

## 环境配置

创建 `.env.local` 文件配置环境变量：

```env
# API 基础地址（生产环境）
VITE_API_BASE_URL=https://api.example.com
```

开发环境下，API 请求会通过 Vite 代理转发到 `http://localhost:8080`。

## API 代理配置

开发环境下，所有 `/api` 请求会被代理到后端服务：

```typescript
// vite.config.ts
server: {
  port: 5173,
  proxy: {
    "/api": {
      target: "http://localhost:8080",
      changeOrigin: true
    }
  }
}
```

## 设计规范

### 主题色彩

项目采用温暖的橙色系作为主色调：

- **主色**: `#ff8a41`
- **强调色**: `#ffcc73`
- **背景色**: `#fff8ee`
- **成功色**: `#12c07b`
- **信息色**: `#4b85f1`

### 响应式断点

- **桌面**: > 1200px
- **平板**: 900px - 1200px
- **移动端**: < 900px

## 后端 API 文档

API 接口文档位于 `docs/` 目录：

- [认证接口](docs/API接口文档_认证.md)
- [搜索接口](docs/API接口文档_搜索.md)
- [用户关系接口](docs/API接口文档_用户关系.md)
- [知文接口](docs/API接口文档_知文.md)
- [计数接口](docs/API接口文档_计数.md)

## License

MIT
