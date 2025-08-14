# 发布指南

## 准备工作

### 1. 更新仓库信息

在 `package.json` 中，将以下占位符替换为实际信息：

- `your-username` → 你的 GitHub 用户名
- 确认邮箱地址正确

### 2. 创建 GitHub 仓库

1. 在 GitHub 上创建新仓库 `semi-theme-vite-plugin`
2. 将代码推送到该仓库

### 3. 注册 npm 账号

如果还没有 npm 账号：

```bash
npm adduser
```

如果已有账号：

```bash
npm login
```

## 发布流程

### 方法一：使用自动化脚本（推荐）

#### 1. 测试发布（推荐先执行）

```bash
cd packages/semi-theme-vite-plugin
npm run release:dry
```

#### 2. 正式发布

```bash
cd packages/semi-theme-vite-plugin
npm run release
```

### 方法二：手动发布

#### 1. 构建项目

```bash
cd packages/semi-theme-vite-plugin
npm run build
```

#### 2. 运行代码检查

```bash
npm run lint
npm run format:check
```

#### 3. 发布到 npm

```bash
npm publish
```

## 版本管理

### 更新版本号

发布前需要更新版本号：

```bash
# 补丁版本 (1.0.0 -> 1.0.1)
npm version patch

# 次要版本 (1.0.0 -> 1.1.0)
npm version minor

# 主要版本 (1.0.0 -> 2.0.0)
npm version major
```

### 发布预发布版本

```bash
# 发布 beta 版本
npm version prerelease --preid=beta
npm publish --tag beta

# 发布 alpha 版本
npm version prerelease --preid=alpha
npm publish --tag alpha
```

## 验证发布

### 1. 检查包信息

```bash
npm view semi-theme-vite-plugin
```

### 2. 在新项目中测试安装

```bash
mkdir test-plugin
cd test-plugin
npm init -y
npm install semi-theme-vite-plugin
```

## 常见问题

### 1. 包名已存在

如果包名 `semi-theme-vite-plugin` 已被占用，需要：

- 选择新的包名（如 `semi-theme-vite-plugin-enhanced`）
- 更新 `package.json` 中的 `name` 字段
- 更新 README.md 中的安装和使用示例

### 2. 权限问题

确保你有发布权限：

```bash
npm whoami  # 检查当前登录用户
```

### 3. 网络问题

如果发布失败，可以尝试：

```bash
npm config set registry https://registry.npmjs.org/
npm publish
```

## 后续维护

### 1. 更新文档

- 保持 README.md 与代码同步
- 记录重要变更

### 2. 处理 Issues

- 及时回复用户问题
- 修复 bug 并发布新版本

### 3. 社区建设

- 添加贡献指南
- 设置 GitHub Actions 进行 CI/CD
- 添加测试用例

## 相关链接

- [npm 发布指南](https://docs.npmjs.com/cli/v8/commands/npm-publish)
- [语义化版本](https://semver.org/lang/zh-CN/)
- [npm 包管理最佳实践](https://docs.npmjs.com/packages-and-modules/contributing-packages-to-the-registry)
