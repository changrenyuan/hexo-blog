---
title: CloudflareWorkers 入门
date: 2025-12-17 09:44:12
tags:
---

# 命令行界面

使用 Cloudflare 开发者平台 CLI Wrangler 设置并部署您的第一个 Worker。

本指南将指导您完成第一个 Worker 的设置和部署。

## 先决条件

[](https://developers.cloudflare.com/workers/get-started/guide/#prerequisites)

1. 注册[Cloudflare 帐户↗](https://dash.cloudflare.com/sign-up/workers-and-pages)。
2. 安装[`Node.js`↗](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)。

Node.js 版本管理器

[使用Volta ↗](https://volta.sh/)或[nvm ↗](https://github.com/nvm-sh/nvm)等 Node 版本管理器可以避免权限问题并更改 Node.js 版本。本指南稍后将讨论的[Wrangler](https://developers.cloudflare.com/workers/wrangler/install-and-update/)需要 Node 版本 10.0`16.17.0`或更高版本。

## 1. 创建一个新的 Worker 项目

[](https://developers.cloudflare.com/workers/get-started/guide/#1-create-a-new-worker-project)

打开终端窗口并运行 C3 来创建您的 Worker 项目。C3 [( `create-cloudflare-cli`) ↗](https://github.com/cloudflare/workers-sdk/tree/main/packages/create-cloudflare)是一个命令行工具，旨在帮助您设置新应用程序并将其部署到 Cloudflare。

- [npm](https://developers.cloudflare.com/workers/get-started/guide/#tab-panel-3563)
- [yarn](https://developers.cloudflare.com/workers/get-started/guide/#tab-panel-3564)
- [pnpm](https://developers.cloudflare.com/workers/get-started/guide/#tab-panel-3565)

终端窗口

```
npm create cloudflare@latest -- my-first-worker
```

设置时，请选择以下选项：

- 对于*“您想从哪里开始？”*，请选择`Hello World example`。
- 对于*“您想使用哪个模板？”*，请选择`Worker only`。
- 对于*“您想使用哪种语言？”*，请选择`JavaScript`。
- 对于“*是否使用 Git 进行版本控制？”*，请选择`Yes`。
- 对于“*是否要部署您的应用程序？”*，请选择`No`（我们将在部署前进行一些更改）。

现在，您已经创建了一个新项目。请进入该项目文件夹。

终端窗口

```
cd my-first-worker
```

C3 创建了哪些文件？

在您的项目目录中，C3 将生成以下内容：

- `wrangler.jsonc`：您的[Wrangler](https://developers.cloudflare.com/workers/wrangler/configuration/#sample-wrangler-configuration)配置文件。
- `index.js`（在）：一个用[ES 模块](https://developers.cloudflare.com/workers/reference/migrate-to-module-workers/)`/src`语法编写的最小`'Hello World!'`Worker 。[](https://developers.cloudflare.com/workers/reference/migrate-to-module-workers/)
- `package.json`：一个最小化的Node依赖配置文件。
- `package-lock.json`：请参阅[↗](https://docs.npmjs.com/cli/v9/configuring-npm/package-lock-json)[`npm`上的文档`package-lock.json`](https://docs.npmjs.com/cli/v9/configuring-npm/package-lock-json)。
- `node_modules`：请参阅[`npm`文档`node_modules`↗](https://docs.npmjs.com/cli/v7/configuring-npm/folders#node-modules)。

如果我已经有一个项目在 Git 仓库中了怎么办？

除了使用 C3 模板创建新项目外，C3 还支持从现有的 Git 仓库创建新项目。要从现有的 Git 仓库创建新项目，请打开终端并运行以下命令：

终端窗口

```
npm create cloudflare@latest -- --template <SOURCE>
```

`<SOURCE>`可以是以下任何一种情况：

- `user/repo`（GitHub）
- `git@github.com:user/repo`
- `https://github.com/user/repo`
- `user/repo/some-template`（子目录）
- `user/repo#canary`（分支）
- `user/repo#1234abcd`（提交哈希）
- `bitbucket:user/repo`(Bitbucket)
- `gitlab:user/repo`（GitLab）

为满足 Cloudflare Workers 的要求，您现有的模板文件夹至少必须包含以下文件：

- `package.json`
- `wrangler.jsonc` [请参阅 Wrangler 配置示例](https://developers.cloudflare.com/workers/wrangler/configuration/#sample-wrangler-configuration)
- `src/`包含一个从以下位置引用的工作脚本`wrangler.jsonc`

## 2. 使用 Wrangler CLI 进行开发

[](https://developers.cloudflare.com/workers/get-started/guide/#2-develop-with-wrangler-cli)

C3 默认会在 Workers 项目中安装[Wrangler](https://developers.cloudflare.com/workers/wrangler/install-and-update/)（Workers 的命令行界面）。Wrangler 可用于[创建](https://developers.cloudflare.com/workers/wrangler/commands/#init)、[测试](https://developers.cloudflare.com/workers/wrangler/commands/#dev)和[部署](https://developers.cloudflare.com/workers/wrangler/commands/#deploy)Workers 项目。

创建第一个 Worker 后，[`wrangler dev`](https://developers.cloudflare.com/workers/wrangler/commands/#dev)在项目目录中运行命令以启动本地服务器，用于开发 Worker。这样您就可以在开发过程中在本地预览 Worker。

终端窗口

```
npx wrangler dev
```

如果您之前从未使用过 Wrangler，它将打开您的网络浏览器，以便您登录您的 Cloudflare 帐户。

请访问[http://localhost:8787 ↗](http://localhost:8787/)查看您的 Worker。

浏览器有问题吗？

如果您在此步骤中遇到问题，或者您无法访问浏览器界面，请参阅[`wrangler login`](https://developers.cloudflare.com/workers/wrangler/commands/#login)文档。

## 3. 编写代码

[](https://developers.cloudflare.com/workers/get-started/guide/#3-write-code)

新项目生成并运行后，您就可以开始编写和编辑代码了。

找到该`src/index.js`文件。该文件`index.js`将填充以下代码：

原始 index.js

```
export default {  async fetch(request, env, ctx) {    return new Response("Hello World!");  },};
```

代码说明

这段代码块由几个不同的部分组成。

已更新 index.js

```
export default {  async fetch(request, env, ctx) {    return new Response("Hello World!");  },};
```

`export default`[定义JavaScript 模块](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules#default_exports_versus_named_exports)需要 JavaScript 语法[↗](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules#default_exports_versus_named_exports)。您的 Worker 必须默认导出一个对象，该对象包含与您的 Worker 应处理的事件相对应的属性。

index.js

```
export default {  async fetch(request, env, ctx) {    return new Response("Hello World!");  },};
```

当您的 Worker 收到 HTTP 请求时，将调用此[`fetch()`处理程序](https://developers.cloudflare.com/workers/runtime-apis/handlers/fetch/)。您可以在导出的对象中定义其他事件处理程序，以响应不同类型的事件。例如，添加一个[`scheduled()`处理程序来响应通过](https://developers.cloudflare.com/workers/runtime-apis/handlers/scheduled/)[Cron 触发器](https://developers.cloudflare.com/workers/configuration/cron-triggers/)调用 Worker 的情况。

此外，`fetch`处理程序始终会收到三个参数：[`request`，`env`和`context`](https://developers.cloudflare.com/workers/runtime-apis/handlers/fetch/)。

index.js

```
export default {  async fetch(request, env, ctx) {    return new Response("Hello World!");  },};
```

Workers 运行时期望`fetch`处理程序返回一个`Response`对象或一个解析为`Response`对象的 Promise。在本例中，您将返回一个`Response`包含字符串的新对象`"Hello World!"`。

将当前文件中的内容替换`index.js`为以下内容，即可更改文本输出。

index.js

```
export default {  async fetch(request, env, ctx) {    return new Response("Hello Worker!");  },};
```

然后保存文件并重新加载页面。你的 Worker 的输出将变为新文本。

没有明显变化？

如果您的工作进程的输出没有变化，请确保：

1. 您已保存更改`index.js`。
2. 你有`wrangler dev`跑步机。
3. 您已重新加载浏览器。

## 4. 部署你的项目

[](https://developers.cloudflare.com/workers/get-started/guide/#4-deploy-your-project)

通过 Wrangler 将 Worker 部署到`*.workers.dev`子域或[自定义域](https://developers.cloudflare.com/workers/configuration/routing/custom-domains/)。

终端窗口

```
npx wrangler deploy
```

如果您尚未配置任何子域或域，Wrangler 将在发布过程中提示您进行设置。

在以下位置预览您的员工`<YOUR_WORKER>.<YOUR_SUBDOMAIN>.workers.dev`：
