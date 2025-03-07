# Flutter Docker 构建镜像

这个仓库包含一个 Dockerfile 和 GitHub Action 配置，用于构建 Flutter 开发环境的 Docker 镜像。

## 功能

- 当新的 tag 被推送到仓库时，自动构建 Docker 镜像
- 使用推送的 tag 作为 Flutter 版本
- 将构建好的镜像推送到 Coding Docker Registry

## 使用方法

1. 在仓库设置中添加以下 secrets：
   - `CODINGHUB_USERNAME`: Coding Docker Registry 的用户名
   - `CODINGHUB_TOKEN`: Coding Docker Registry 的密码/令牌

2. 创建并推送一个新的 tag，格式应与 Flutter 版本号匹配，例如：
   ```bash
   git tag 3.22.3
   git push origin 3.22.3
   ```

3. GitHub Action 将自动触发，构建 Docker 镜像并推送到：
   `code2code-docker.pkg.coding.net/puupees/k8s/flutter-build-runner:3.22.3`

## 自定义

如果需要修改 Dockerfile 或 GitHub Action 配置，可以编辑以下文件：
- `Dockerfile`: 修改 Docker 镜像的构建过程
- `.github/workflows/docker-build.yml`: 修改 GitHub Action 工作流程 