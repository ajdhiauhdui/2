# 个人博客系统

一个基于Vue 3 + TypeScript + Express + MySQL的个人博客系统，支持文章发布、评论互动、数据统计等功能。

## 功能特点

- 用户认证系统（注册、登录、个人资料管理）
- 文章管理（发布、编辑、删除）
- 分类与标签系统
- 评论互动功能
- 点赞和收藏文章
- 用户关注功能
- 搜索功能（支持全文搜索）
- 数据统计分析
- 响应式设计，适配不同设备

## 技术栈

### 前端
- Vue 3 + Composition API
- TypeScript
- Pinia (状态管理)
- Vue Router
- Element Plus (UI组件库)
- Axios (HTTP请求)
- WangEditor (富文本编辑器)

### 后端
- Node.js
- Express
- MySQL
- JWT (认证)
- Bcrypt (密码加密)
- Multer (文件上传)

## 数据库设计

主要数据表:
- users (用户表)
- articles (文章表)
- categories (分类表)
- tags (标签表)
- comments (评论表)
- article_category (文章分类关联表)
- article_tag (文章标签关联表)
- article_likes (文章点赞表)
- article_favorites (文章收藏表)
- user_follows (用户关注表)
- statistics (统计数据表)

## 安装与运行

### 准备工作

1. 确保已安装Node.js环境 (推荐v16+)
2. 确保已安装并启动MySQL数据库 (推荐v8.0+)
3. 创建数据库`qimo`
4. 安装pnpm: `npm install -g pnpm`

### 安装依赖

```bash
# 安装项目依赖
pnpm install
```

### 初始化数据库

在MySQL中执行`server/db/init.sql`脚本初始化数据库表和测试数据。

### 运行项目

有两种启动方式：

```bash
# 方式1: 同时启动前端和后端 (推荐)
pnpm start

# 方式2: 分别启动前端和后端
# 启动前端开发服务器
pnpm dev

# 启动后端服务器
pnpm backend
```

前端默认运行在 http://localhost:5173  
后端默认运行在 http://localhost:3000

### 测试账号

管理员账号:
- 用户名: admin
- 密码: 123456

## 项目结构

```
├── public/             # 静态资源文件
├── server/             # 后端代码
│   ├── config/         # 配置文件
│   ├── controllers/    # 控制器
│   ├── db/             # 数据库相关
│   ├── middleware/     # 中间件
│   ├── routes/         # 路由定义
│   ├── uploads/        # 上传文件存储
│   └── app.js          # 服务器入口文件
├── src/                # 前端代码
│   ├── assets/         # 静态资源
│   ├── components/     # 组件
│   ├── router/         # 路由配置
│   ├── stores/         # Pinia状态
│   ├── types/          # TypeScript类型定义
│   ├── views/          # 页面视图
│   ├── App.vue         # 根组件
│   └── main.ts         # 前端入口文件
├── .gitignore          # Git忽略文件
├── index.html          # HTML模板
├── package.json        # 项目依赖
├── tsconfig.json       # TypeScript配置
└── vite.config.ts      # Vite配置
```

## 主要功能模块

### 首页
- 文章列表展示
- 分类与标签导航
- 搜索功能

### 文章详情
- 文章内容展示
- 评论系统
- 点赞和收藏功能

### 用户系统
- 注册和登录
- 个人资料管理
- 用户文章管理
- 关注与粉丝功能

### 统计分析
- 浏览量统计
- 用户活跃度分析
- 内容热度分析

## API接口文档

### 用户相关

- POST /api/users/register - 用户注册
- POST /api/users/login - 用户登录
- GET /api/users/me - 获取当前用户信息
- PUT /api/users/me - 更新用户信息
- PUT /api/users/change-password - 修改密码
- GET /api/users/:id - 获取指定用户信息
- GET /api/users/:id/articles - 获取用户文章列表

### 文章相关

- GET /api/articles - 获取文章列表
- GET /api/articles/:id - 获取文章详情
- POST /api/articles - 创建文章
- PUT /api/articles/:id - 更新文章
- DELETE /api/articles/:id - 删除文章

### 评论相关

- GET /api/comments/article/:articleId - 获取文章评论
- POST /api/comments/article/:articleId - 添加评论
- DELETE /api/comments/:id - 删除评论
- PUT /api/comments/:id - 更新评论

### 分类相关

- GET /api/categories - 获取所有分类
- GET /api/categories/:id - 获取分类详情
- POST /api/categories - 创建分类
- PUT /api/categories/:id - 更新分类
- DELETE /api/categories/:id - 删除分类
- GET /api/categories/:id/articles - 获取分类下的文章

### 标签相关

- GET /api/tags - 获取所有标签
- GET /api/tags/:id - 获取标签详情
- POST /api/tags - 创建标签
- PUT /api/tags/:id - 更新标签
- DELETE /api/tags/:id - 删除标签
- GET /api/tags/:id/articles - 获取标签下的文章

### 互动相关

- POST /api/likes/article/:articleId - 点赞文章
- DELETE /api/likes/article/:articleId - 取消点赞
- POST /api/favorites/article/:articleId - 收藏文章
- DELETE /api/favorites/article/:articleId - 取消收藏
- POST /api/follows/user/:userId - 关注用户
- DELETE /api/follows/user/:userId - 取消关注

### 搜索相关

- GET /api/search - 全站搜索
- GET /api/search/articles - 搜索文章
- GET /api/search/users - 搜索用户

### 统计相关

- GET /api/statistics - 获取全站统计数据
- GET /api/statistics/articles - 获取文章统计数据
- GET /api/statistics/users - 获取用户统计数据

### 文件上传

- POST /api/upload - 上传图片文件

## 前端路由

- `/` - 首页
- `/home` - 文章列表页
- `/article/:id` - 文章详情页
- `/article/create` - 创建文章页
- `/article/edit/:id` - 编辑文章页
- `/search` - 搜索结果页
- `/profile/:id` - 用户个人资料页
- `/manage` - 用户文章管理页
- `/statistics` - 数据统计页
- `/auth` - 认证页
- `/login` - 登录页
- `/register` - 注册页

