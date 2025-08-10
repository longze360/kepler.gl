# Kepler.gl 本地部署指南 (NVM 环境)

本指南将引导您如何在本地环境中，使用 [NVM (Node Version Manager)](https://github.com/nvm-sh/nvm) 来设置、安装并运行 kepler.gl 项目。

## 1. 先决条件

在开始之前，请确保您的系统已安装以下工具：

-   **Git**: 用于克隆项目代码库。
-   **NVM**: 用于管理 Node.js 版本。
-   **Yarn**: kepler.gl 使用 Yarn 作为包管理器。在设置好 Node.js 环境后，可以通过 `npm install -g yarn` 安装。
-   **Mapbox 访问令牌 (Access Token)**: kepler.gl 使用 Mapbox 来渲染底图，因此您需要一个有效的访问令牌。
    -   您可以访问 [Mapbox 官网](https://www.mapbox.com/) 免费注册并创建一个。

## 2. 安装和配置

请按照以下步骤操作：

### 步骤 1: 克隆项目

首先，使用 Git 克隆 kepler.gl 的代码库到您的本地计算机。

```bash
git clone https://github.com/keplergl/kepler.gl.git
cd kepler.gl
```

### 步骤 2: 使用 NVM 设置 Node.js 版本

kepler.gl 项目在 `.nvmrc` 文件中指定了推荐的 Node.js 版本。您可以使用 nvm 轻松安装并切换到该版本。

```bash
# nvm 会自动读取 .nvmrc 文件并安装指定的 Node.js 版本
nvm install

# 切换到该版本
nvm use
```

运行 `node -v` 确认当前 Node.js 版本是否正确 (应为 `v18.18.2` 或 `.nvmrc` 中指定的版本)。

### 步骤 3: 配置 Mapbox 访问令牌

项目需要一个 Mapbox 访问令牌来加载地图瓦片。您需要将令牌配置在环境变量中。

1.  复制环境变量模板文件：

    ```bash
    cp .env.template .env
    ```

2.  编辑新创建的 `.env` 文件，将 `YOUR_MAPBOX_TOKEN` 替换为您自己的 Mapbox 访问令牌。

    ```plaintext
    # .env
    MapboxAccessToken="pk.eyJ1IjoibXl1c2VybmFtZSIsImEiOiJja2Ew...remainder_of_your_token"
    ```

### 步骤 4: 安装项目依赖

kepler.gl 是一个 monorepo 项目，包含多个子包。项目提供了一个 `bootstrap` 脚本来正确地安装所有依赖。

```bash
# 使用 yarn bootstrap 安装所有依赖并初始化子模块
yarn bootstrap
```

此过程可能需要一些时间，因为它会下载所有必需的 npm 包。

## 3. 运行开发服务器

完成所有安装和配置后，您可以运行 `start` 脚本来启动本地开发服务器。

```bash
# 启动示例应用 (demo-app)
yarn start
```

该命令会执行以下操作：
-   启动一个本地开发服务器。
-   编译项目代码。
-   完成后，它会自动在您的默认浏览器中打开一个页面，通常是 `http://localhost:8080`。

您现在应该能看到 kepler.gl 的界面，并可以开始进行交互和开发了。

---

祝您开发愉快！
