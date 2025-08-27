#### 项目整体文件说明
- `config` 配置文件目录
  - `default.json` 默认配置文件（其中包含数据库配置，jwt配置）
- `dao` 数据访问层，存放对数据库的增删改查操作
  - `DAO.js` 提供的公共访问数据库的方法
- `models` 存放具体数据库 ORM 模型文件
- `modules` 当前项目模块
  - `authorization.js` API权限验证模块
  - `database.js` 数据库模块（数据库加载基于 nodejs-orm2 库加载）
  - `passport.js` 基于 passport 模块的登录搭建
  - `resextra.js` API 统一返回结果接口
- `node_modules` 项目依赖的第三方模块
- `routes` 统一路由
  - `api` 提供 api 接口
  - `mapp` 提供移动APP界面
  - `mweb` 提供移动web站点
- `services` 服务层，业务逻辑代码在这一层编写，通过不同的接口获取的数据转换成统一的前端所需要的数据
- `app.js` 主项目入口文件
- `package.json` 项目配置文件

# 商城后台管理系统 API 服务

> 基于 Node.js + Express + MySQL 构建的商城后台管理系统API服务端

## 项目简介

本项目是一个完整的商城后台管理系统API服务，提供了用户管理、商品管理、订单管理、权限管理等核心功能。采用MVC架构模式，支持JWT认证、角色权限控制、文件上传等功能。

## 技术栈

- **运行环境**: Node.js
- **Web框架**: Express.js
- **数据库**: MySQL
- **ORM**: node-orm2
- **身份认证**: JWT + Passport.js
- **文件上传**: Multer + 富文本编辑器(UEditor)
- **测试框架**: Mocha + Chai
- **日志管理**: log4js
- **其他工具**: lodash、underscore、busboy等

## 项目结构

```
├── config/                    # 配置文件目录
│   ├── default.json          # 默认配置文件（数据库、JWT、上传配置）
│   └── ueditor.config.js     # 富文本编辑器配置
├── dao/                      # 数据访问层(DAO)
│   ├── DAO.js               # 公共数据库访问方法
│   ├── AttributeDAO.js      # 属性数据访问
│   ├── GoodAttributeDAO.js  # 商品属性数据访问
│   ├── ManagerDAO.js        # 管理员数据访问
│   └── PermissionAPIDAO.js  # 权限API数据访问
├── models/                   # 数据模型层
│   ├── AttributeModel.js    # 属性模型
│   ├── CategoryModel.js     # 分类模型
│   ├── GoodModel.js         # 商品模型
│   ├── ManagerModel.js      # 管理员模型
│   ├── OrderModel.js        # 订单模型
│   ├── PermissionModel.js   # 权限模型
│   ├── RoleModel.js         # 角色模型
│   └── ...                  # 其他模型文件
├── modules/                  # 核心模块
│   ├── authorization.js     # API权限验证模块
│   ├── database.js          # 数据库连接模块
│   ├── passport.js          # Passport认证策略
│   ├── resextra.js          # 统一响应结果模块
│   ├── logger.js            # 日志模块
│   ├── Logistics.js         # 物流查询模块
│   └── ueditor.js           # 富文本编辑器后端支持
├── routes/api/private/v1/    # API路由层
│   ├── categories.js        # 分类管理API
│   ├── goods.js             # 商品管理API
│   ├── users.js             # 用户管理API
│   ├── roles.js             # 角色管理API
│   ├── orders.js            # 订单管理API
│   ├── reports.js           # 报表统计API
│   ├── rights.js            # 权限管理API
│   ├── upload.js            # 文件上传API
│   └── menus.js             # 菜单管理API
├── services/                 # 业务逻辑层
│   ├── AttributeService.js  # 属性业务逻辑
│   ├── CategoryService.js   # 分类业务逻辑
│   ├── GoodService.js       # 商品业务逻辑
│   ├── ManagerService.js    # 管理员业务逻辑
│   ├── OrderService.js      # 订单业务逻辑
│   ├── RoleService.js       # 角色业务逻辑
│   └── ...                  # 其他业务逻辑
├── test/                     # 测试文件
│   ├── api/private/         # API测试
│   └── configs/             # 测试配置
├── public/ueditor/          # 富文本编辑器静态资源
├── app.js                   # 应用程序入口文件
└── package.json             # 项目依赖配置
```

## 核心功能

### 1. 用户管理
- 管理员账户的增删改查
- 用户状态管理（启用/禁用）
- 用户角色分配
- 密码加密存储

### 2. 权限管理
- 基于角色的权限控制（RBAC）
- API接口权限验证
- JWT Token认证
- 路由级别权限控制

### 3. 商品管理
- 商品信息的CRUD操作
- 商品分类管理
- 商品属性管理
- 商品图片上传

### 4. 订单管理
- 订单查询和状态管理
- 物流信息查询
- 订单统计报表

### 5. 文件上传
- 支持多种文件格式上传
- 富文本编辑器集成
- 图片处理和存储

## 快速开始

### 环境要求
- Node.js >= 8.0
- MySQL >= 5.7
- npm 或 yarn

### 安装依赖
```bash
npm install
```

### 数据库配置
1. 创建MySQL数据库
2. 修改 `config/default.json` 中的数据库配置：
```json
{
  "db_config": {
    "protocol": "mysql",
    "host": "127.0.0.1",
    "database": "your_database_name",
    "user": "your_username",
    "password": "your_password",
    "port": 3306
  }
}
```

### 启动应用
```bash
npm start
```

应用将在 `http://localhost:8888` 启动

## API 接口说明

### 认证接口
- `POST /api/private/v1/login` - 管理员登录

### 用户管理
- `GET /api/private/v1/users` - 获取用户列表
- `GET /api/private/v1/users/:id` - 获取指定用户信息
- `POST /api/private/v1/users` - 创建新用户
- `PUT /api/private/v1/users/:id` - 更新用户信息
- `DELETE /api/private/v1/users/:id` - 删除用户
- `PUT /api/private/v1/users/:id/role` - 分配用户角色
- `PUT /api/private/v1/users/:id/state/:state` - 更新用户状态

### 角色权限管理
- `GET /api/private/v1/roles` - 获取角色列表
- `POST /api/private/v1/roles` - 创建角色
- `GET /api/private/v1/rights` - 获取权限列表

### 商品管理
- `GET /api/private/v1/goods` - 获取商品列表
- `POST /api/private/v1/goods` - 添加商品
- `GET /api/private/v1/categories` - 获取商品分类

### 订单管理
- `GET /api/private/v1/orders` - 获取订单列表
- `GET /api/private/v1/kuaidi/:orderno` - 查询物流信息

### 文件上传
- `POST /api/private/v1/upload` - 文件上传接口

## 中间件说明

### 1. 跨域处理
所有API接口都已配置CORS，支持跨域访问

### 2. 身份认证
使用JWT Token进行身份认证，需要在请求头中携带：
```
Authorization: Bearer <token>
```

### 3. 权限验证
基于角色的权限控制，每个API接口都会验证用户权限

### 4. 统一响应格式
所有API接口返回格式统一：
```json
{
  "data": {},
  "meta": {
    "msg": "操作成功",
    "status": 200
  }
}
```

## 测试

### 运行测试
```bash
npm test
```

### 测试覆盖
项目包含以下测试：
- 用户管理API测试
- 登录认证测试
- 角色权限测试
- 商品管理测试

## 部署说明

### 生产环境配置
1. 修改 `config/default.json` 中的配置项
2. 设置环境变量
3. 配置反向代理（如Nginx）
4. 启用日志记录

### Docker部署
```bash
# 构建镜像
docker build -t shop-api .

# 运行容器
docker run -p 8888:8888 shop-api
```

## 开发规范

### 目录结构说明
- `dao/` - 数据访问层，负责与数据库交互
- `models/` - 数据模型定义
- `services/` - 业务逻辑层，处理具体业务
- `routes/` - 路由层，定义API接口
- `modules/` - 公共模块和中间件

### 代码规范
- 使用ES6+语法
- 统一错误处理
- 参数验证
- 日志记录

## 常见问题

### 1. 数据库连接失败
检查数据库配置和网络连接

### 2. 权限验证失败
确认JWT Token是否正确，用户角色是否有对应权限

### 3. 文件上传失败
检查上传目录权限和文件大小限制

## 贡献指南

1. Fork 项目
2. 创建特性分支
3. 提交更改
4. 推送到分支
5. 创建 Pull Request

## 许可证

MIT License

## 更新日志

### v0.0.0
- 初始版本发布
- 实现基础用户管理功能
- 实现权限控制系统
- 实现商品和订单管理
- 集成富文本编辑器
- 添加物流查询功能