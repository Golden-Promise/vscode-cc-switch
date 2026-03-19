# 🚀 VS Code + cc-Switch 使用教程

本教程旨在帮助开发者通过 **VS Code** 结合 **cc-Switch** 工具，快速实现 Claude Code 对第三方模型（API）的无缝调用与灵活配置。

---

## 💻 一、安装 VS Code（若已安装，可跳过此步骤） 

* 🌐 **官方下载地址**：[https://code.visualstudio.com/Download](https://code.visualstudio.com/Download)
* 📥 请根据您的操作系统选择合适的版本下载并安装，如下图所示：

<img src="image/Claude%20code使用教程1.png" alt="Claude code使用教程1" width="80%" />

---

## 🔌 二、安装 cc-Switch

**1. 访问 GitHub 开源仓库**：[https://github.com/farion1231/cc-switch](https://github.com/farion1231/cc-switch)

**2. 下载最新的发行版本（Release）**：
* 进入仓库后，点击右侧的 `Releases` 区域，或直接访问链接：[Releases 页面](https://github.com/farion1231/cc-switch/releases)

<img src="image/Claude%20code使用教程2.png" alt="Claude code使用教程2" width="80%" />

* 在最新版本的 `Assets` 列表中，选择对应的系统版本进行下载：

<img src="image/Claude%20code使用教程3.png" alt="Claude code使用教程3" width="80%" />

**3. 执行安装**：
打开刚才下载的 `.msi` 安装包（Installer 程序包），按照向导提示完成安装即可：

<img src="image/Claude%20code使用教程.png" alt="Claude code使用教程" width="80%" />

**4. 启动程序**：
安装完成后，打开 cc-Switch 客户端，准备后续配置：

<img src="image/Claude%20code使用教程7.png" alt="Claude code使用教程7" width="80%" />

---

## 🧩 三、在 VS Code 中安装 Claude Code 扩展

**1. 打开扩展商店**：在 VS Code 左侧活动栏中点击“扩展”图标（或使用快捷键 `Ctrl+Shift+X`）。

<img src="image/Claude%20code使用教程5.png" alt="Claude code使用教程5" width="80%" />

**2. 搜索并安装扩展**：在搜索框中输入 `Claude Code` 并点击安装。

<img src="image/Claude%20code使用教程6.png" alt="Claude code使用教程6" width="80%" />

**3. 验证安装**：扩展安装完成后，点击 VS Code 右侧边栏的 Claude Code 图标。若出现红框所示的侧边栏界面，即说明安装成功：

<img src="image/Claude%20code使用教程8.png" alt="Claude code使用教程8" width="80%" />

---

## ⚙️ 四、通过 cc-Switch 调用第三方模型

### 💡 （1）原理解析
* **为何使用 cc-Switch**：
    * 免去手动编辑复杂 `settings.json` 配置文件的繁琐。
    * 支持预存多套 API 方案，实现一键无缝切换。
    * 轻松接入各路中转站，完美适配各类第三方 API 聚合服务。
* **核心机制**：
    * cc-Switch 在底层动态覆盖了 `ANTHROPIC_BASE_URL` 和 `ANTHROPIC_API_KEY` 这两个关键环境变量。它将 Claude Code 原本发往官方的请求，“拦截”并重定向至您配置的第三方接口，从而在底层实现模型的无缝替换。

### 🔑 （2）前置准备
**① 获取调用凭证**：
在开始配置前，需要从第三方平台获取以下信息（本文以**硅基流动 (SiliconFlow)** 为例，其他支持的模型或中转平台配置逻辑完全一致）：
* **API Key**（密钥）
* **Base URL**（接口地址）
* **模型名称**

**② 创建 API 密钥**：
登录 [硅基流动官网](https://siliconflow.com)，在控制台生成您的 API 密钥：

<img src="image/Claude%20code使用教程9.png" alt="Claude code使用教程9" width="80%" />

**③ 获取模型名称**：
进入模型广场，选择您需要的模型，点击模型名称即可复制：

<img src="image/Claude%20code使用教程10.png" alt="Claude code使用教程10" width="80%" />

**④ 确认 Base URL**：
查阅官方 API 接口文档获取 Base URL。硅基流动的地址通常为 `https://api.siliconflow.cn/`（其他中转平台请参考其官方说明）：

<img src="image/Claude%20code使用教程11.png" alt="Claude code使用教程11" width="80%" />

### 🏠 （3）本地环境配置指南

**① 添加供应商**：
回到 cc-Switch 客户端，点击添加新的服务供应商：

<img src="image/Claude%20code使用教程12.png" alt="Claude code使用教程12" width="80%" />

**② 填写配置信息**：
* 按照下图指示进入配置页面：

<img src="image/Claude%20code使用教程13.png" alt="Claude code使用教程13" width="80%" />

* 向下滚动页面，将刚才获取的凭证填入对应位置：

<img src="image/Claude%20code使用教程14.png" alt="Claude code使用教程14" width="80%" />

<img src="image/Claude%20code使用教程15.png" alt="Claude code使用教程15" width="80%" />

* 其他高级配置可按需修改。最后请核对红框内的核心信息，确认无误后点击添加：

<img src="image/Claude%20code使用教程16.png" alt="Claude code使用教程16" width="80%" />

**③ 启动 Vibe Coding**：
重新打开 VS Code 中的 Claude Code 扩展。如果无需登录账号，直接跳转至对话窗口，即说明配置大功告成，您可以开始使用啦！

<img src="image/Claude%20code使用教程17.png" alt="Claude code使用教程17" width="80%" />

### ☁️ （4）远程环境（Remote - SSH）配置指南

**① 开启本地代理服务**：
在 cc-Switch 中开启本地代理，并务必记住生成的服务地址与端口：

<img src="image/Claude%20code使用教程18.png" alt="Claude code使用教程18" width="80%" />

<img src="image/Claude%20code使用教程19.png" alt="Claude code使用教程19" width="80%" />

**② 验证代理状态**：
* 点击上图步骤②中的图标，进入终端：

<img src="image/Claude%20code使用教程20.png" alt="Claude code使用教程20" width="80%" />

* 在终端中执行以下指令。若弹出的文本文件中包含代理信息，说明代理开启成功。请复制红框中的内容备用：
```cmd
notepad "%USERPROFILE%\.claude\settings.json"
```

<img src="image/Claude%20code使用教程21.png" alt="Claude code使用教程21" width="80%" />

**③ 远程配置 Claude Code（需提前安装 VS Code 的 Remote - SSH 插件）**：
* 编辑 VS Code 远程连接配置文件，添加 `RemoteForward` 参数进行端口转发，格式请参考下图：

<img src="image/Claude%20code使用教程22.png" alt="Claude code使用教程22" width="80%" />

<img src="image/Claude%20code使用教程23.png" alt="Claude code使用教程23" width="80%" />

* 在远程服务器上安装 Claude Code 扩展：

<img src="image/Claude%20code使用教程24.png" alt="Claude code使用教程24" width="50%" />

* 对远程扩展进行环境配置：

<img src="image/Claude%20code使用教程25.png" alt="Claude code使用教程25" width="80%" />

* 将之前复制的代理地址与密钥填入空括号 `[]` 中，完成后的效果参考红框内容：

<img src="image/Claude%20code使用教程26.png" alt="Claude code使用教程26" width="80%" />

**④ 完成配置并运行**：
操作逻辑与本地运行一致。点击右侧边栏的 Claude Code 图标，若直接进入对话界面，说明远程配置成功。现在，尽情享受您的远程 Vibe Coding 体验吧！

<img src="image/Claude%20code使用教程111.png" alt="Claude code使用教程111" width="80%" />