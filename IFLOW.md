# iFlow 项目上下文文件

## 项目概述

这是一个基于 **Vue 3 + Vite** 构建的企业官网项目，用于展示公司信息、招聘信息、活动策划和团队介绍。项目采用现代化的前端技术栈，支持多语言国际化、用户认证和角色权限管理。

### 核心技术栈

- **Vue 3** - 使用 Composition API 构建响应式应用
- **Vite 5** - 下一代前端构建工具，提供快速的开发体验
- **Vue Router 4** - 官方路由管理器，支持路由守卫和权限控制
- **Element Plus 2** - Vue 3 UI 组件库
- **ECharts 6** - 数据可视化图表库
- **Vue I18n 9** - 国际化支持（中文/英文）
- **认证系统** - 基于 Token 的身份验证和 RBAC 权限管理

## 项目结构

```
chenfeng-c.github.io/
├── src/
│   ├── api/                    # API 接口层
│   │   ├── index.js           # API 统一入口（当前使用 Mock 数据）
│   │   ├── mock.js            # Mock API 实现
│   │   └── README.md          # API 文档
│   ├── assets/                 # 静态资源
│   │   └── css/               # 全局样式文件
│   ├── components/             # 可复用组件
│   │   ├── charts/            # 图表组件
│   │   ├── icons/             # 图标组件
│   │   ├── HeaderBanner.vue   # 页头横幅
│   │   ├── Navigation.vue     # 导航栏
│   │   ├── PageHeader.vue     # 页面标题
│   │   └── UserProfile.vue    # 用户资料组件
│   ├── i18n/                   # 国际化配置
│   │   └── index.js           # i18n 初始化
│   ├── locales/                # 语言包
│   │   ├── zh.json            # 中文语言包
│   │   └── en.json            # 英文语言包
│   ├── router/                 # 路由配置
│   │   └── index.js           # 路由定义和守卫
│   ├── store/                  # 状态管理
│   │   └── auth.js            # 认证状态管理
│   ├── utils/                  # 工具函数
│   │   ├── colors.js          # 颜色工具
│   │   ├── data.js            # 数据工具
│   │   └── i18n-helper.js     # 国际化辅助函数
│   ├── views/                  # 页面组件
│   │   ├── Home.vue           # 首页
│   │   ├── About.vue          # 关于页面
│   │   ├── Jobs.vue           # 招聘页面
│   │   ├── Events.vue         # 活动页面
│   │   ├── Team.vue           # 团队页面
│   │   ├── Login.vue          # 登录页面
│   │   ├── Register.vue       # 注册页面
│   │   ├── Profile.vue        # 个人资料页面
│   │   ├── AdminDashboard.vue # 管理后台
│   │   ├── AccessDenied.vue   # 访问拒绝页面
│   │   └── ExternalPortal.vue # 外部门户
│   ├── App.vue                 # 根组件
│   └── main.js                 # 应用入口
├── public/                     # 公共静态资源
│   ├── CNAME                   # GitHub Pages 自定义域名
│   ├── favicon.svg            # 网站图标
│   └── logo.svg               # Logo 文件
├── dist/                       # 构建输出目录
├── .github/workflows/          # GitHub Actions 工作流
│   └── deploy.yml             # 自动部署配置
├── index.html                  # HTML 模板
├── vite.config.js             # Vite 配置文件
├── package.json               # 项目依赖配置
└── README.md                  # 项目说明文档
```

## 构建和运行

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
npm run dev
```

- 访问地址：http://localhost:3000
- 支持热模块替换（HMR）
- 自动打开浏览器
- 支持局域网访问

### 生产构建

```bash
npm run build
```

构建输出目录：`dist/`

### 预览生产构建

```bash
npm run preview
```

### 环境变量配置

项目支持通过环境变量控制行为：

- `VITE_USE_MOCK` - 是否使用 Mock API（默认：`true`）
- `VITE_API_BASE_URL` - 真实 API 基础路径

## 开发规范

### 代码风格

- 使用 **Vue 3 Composition API** 编写组件
- 使用 `<script setup>` 语法糖简化代码
- 组件命名采用 PascalCase（如 `UserProfile.vue`）
- 文件命名采用 kebab-case（如 `user-profile.vue`）

### 路由规范

- 所有路由定义在 `src/router/index.js`
- 使用路由守卫进行权限控制：
  - `requiresAuth` - 需要登录
  - `requiresGuest` - 仅限未登录用户
  - `roles` - 需要特定角色（如 `['admin']`）
- 路由跳转使用命名路由（`router.push({ name: 'Home' })`）

### 国际化规范

- 所有用户可见文本必须使用 i18n
- 语言包位于 `src/locales/` 目录
- 支持的语言：`zh-CN`（中文）、`en-US`（英文）
- 使用 `$t('key')` 或 `t('key')` 获取翻译文本

### API 调用规范

- 所有 API 调用通过 `src/api/index.js` 统一导出
- 当前使用 Mock 数据，可通过环境变量切换到真实 API
- API 返回格式：
  ```javascript
  {
    success: boolean,
    message: string,
    data: any
  }
  ```

### 状态管理规范

- 认证状态使用 `src/store/auth.js` 管理
- 用户信息存储在 `localStorage` 中
- Token 验证在应用启动时自动执行

### 样式规范

- 全局样式放在 `src/assets/css/` 目录
- 每个页面组件对应一个样式文件
- 使用 CSS 预处理器（如果需要）
- 响应式设计使用媒体查询，断点：
  - 992px - 平板
  - 768px - 小平板
  - 480px - 手机

### 组件开发规范

- 可复用组件放在 `src/components/` 目录
- 页面组件放在 `src/views/` 目录
- 组件接收 props 时进行类型验证
- 使用 `emits` 声明自定义事件
- 复杂逻辑抽取为 composable

## 主要功能

### 页面功能

1. **首页** (`/`) - 公司概览和主要服务介绍
2. **关于** (`/about`) - 公司详细介绍
3. **招聘** (`/jobs`) - 职位招聘信息
4. **活动** (`/events`) - 公司活动策划
5. **团队** (`/team`) - 团队成员介绍
6. **登录** (`/login`) - 用户登录
7. **注册** (`/register`) - 新用户注册
8. **个人资料** (`/profile`) - 用户个人信息管理（需登录）
9. **管理后台** (`/admin`) - 管理员面板（需 admin 角色）
10. **访问拒绝** (`/unauthorized`) - 权限不足提示页面

### 认证与权限

- 基于 Token 的身份验证
- 支持角色权限管理（RBAC）
- 路由级别的权限控制
- Token 自动验证和刷新
- 登录状态持久化（localStorage）

### 国际化

- 支持中英文切换
- Element Plus 组件库本地化
- 语言切换状态持久化
- 缺失翻译回退机制

### 响应式设计

- 移动优先设计理念
- 支持桌面、平板、手机等多种设备
- 导航栏自适应布局
- 图片和内容自适应

## 部署

项目配置了 GitHub Actions 自动部署到 GitHub Pages：

- 推送到 `main` 分支自动触发部署
- 构建产物部署到 `gh-pages` 分支
- 自定义域名通过 `public/CNAME` 配置

## 注意事项

1. **Mock API** - 当前项目使用 Mock 数据，如需对接真实 API：
   - 修改 `src/api/index.js` 中的 `USE_MOCK` 配置
   - 实现 `src/api/` 下的真实 API 调用
   - 配置环境变量 `VITE_API_BASE_URL`

2. **Token 验证** - 应用启动时会自动验证存储的 Token，确保用户会话有效

3. **ECharts 优化** - 项目已配置代码分割，ECharts 被单独打包以优化加载性能

4. **开发服务器** - 开发服务器配置了 CORS 和热重载，支持局域网访问

5. **构建优化** - 生产构建启用了代码分割、压缩和源码映射，chunk 大小警告限制为 1000KB

## 扩展建议

- 添加单元测试和端到端测试
- 实现真实的后端 API
- 添加更多语言支持
- 优化 SEO（meta 标签、sitemap）
- 添加性能监控和分析
- 实现主题切换（深色模式）