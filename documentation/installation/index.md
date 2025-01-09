# 安装主题


只需几个步骤即可为你的 Hugo 站点安装 **FixIt** 主题。

&lt;!--more--&gt;

1. 在 `hugo.toml` 中配置默认主题为 FixIt，例如 `theme = &#34;FixIt&#34;`
2. 通过以下其中一种方式安装主题

## 先决条件

由于 Hugo 提供的便利性，[Hugo][hugo] 可能是此主题的唯一依赖项。

尽管不是在所有情况下都需要，但是在使用 Hugo 时通常会使用 [Git][git]、[Go][go]、[Dart Sass][dart-sass] 和 [Node.js][node.js]。

Git 用于：

- 从源代码构建 Hugo
- 使用 [Hugo 模块][hugo-modules] 功能
- 将主题安装为 Git 子模块
- 从本地 Git 存储库访问 [提交信息][commit-info]
- 使用 [CloudCannon][cloudcannon]、[Cloudflare Pages][cloudflare-pages]、[GitHub Pages][github-pages]、[GitLab Pages][gitlab-pages] 和 [Netlify][netlify] 等服务托管你的站点

Go 用于：

- 从源代码构建 Hugo
- 使用 Hugo 模块功能

Dart Sass 用于在使用 Sass 语言的最新功能时将 Sass 转译为 CSS。

Node.js 用于：

- 使用 FixIt CLI
- 使用一些自动化工具，例如

请参考相关文档以获取安装说明：

- [Hugo][hugo-install]（扩展版，v 或更高版本）
- [Git][git-install]
- [Go][go-install]
- _[Dart Sass][dart-sass-install]（尚未使用）_
- [Node.js][node-install]（v16.0.0 或更高版本）

## 手动安装 {#manual}

你可以下载主题的 [最新版本 :(fa-regular fa-file-archive fa-fw): .zip 文件][releases] 并将其解压到 `themes` 目录中。

要升级主题，请用新主题替换旧主题。

## Git 克隆 {#git-clone}

这种方式，只需将 [FixIt][fixit] 主题克隆到 `themes` 目录中即可。

```bash
git clone https://github.com/hugo-fixit/FixIt.git themes/FixIt
```

通过从存储库中拉取最新提交来升级主题。

```bash
cd themes/FixIt
git pull
```

## Git 子模块 {#git-submodule}

&lt;!-- markdownlint-disable-next-line no-bare-urls --&gt;
{{&lt; link &#34;https://github.com/hugo-fixit/hugo-fixit-starter1/generate&#34; &#34;点击快速创建博客！&#34; &#34;一个基于 Git 子模块创建 Hugo FixIt 站点的快速启动模板。&#34; true &#34;fa-solid fa-screwdriver-wrench&#34; &gt;}}

在当前目录中初始化一个空的 Git 存储库。

```bash
git init
```

将 [FixIt][fixit] 添加到你的项目中，作为一个 [Git 子模块][git-submodule] 存储在 `themes` 目录中的。

```bash
git submodule add https://github.com/hugo-fixit/FixIt.git themes/FixIt
```

要使用 `dev` 分支上的版本，可以使用以下命令：

```bash
git submodule add -b dev https://github.com/hugo-fixit/FixIt.git themes/FixIt

# 或者，将子模块分支从 `master` 切换到 `dev`：
git submodule set-branch -b dev themes/FixIt
```

使用以下命令升级主题：

```bash
git submodule update --remote --merge themes/FixIt
```

## Hugo 模块 {#hugo-module}

&lt;!-- markdownlint-disable-next-line no-bare-urls --&gt;
{{&lt; link &#34;https://github.com/hugo-fixit/hugo-fixit-starter/generate&#34; &#34;点击快速创建博客！&#34; &#34;一个基于 Hugo 模块创建 Hugo FixIt 站点的快速启动模板。&#34; true &#34;fa-solid fa-screwdriver-wrench&#34; &gt;}}

{{&lt; admonition tip &gt;}}
以这种方式，无需要在 `hugo.toml` 中配置 `theme = &#34;FixIt&#34;`。
{{&lt; /admonition &gt;}}

将 [Hugo 模块][hugo-modules] 用于主题的最简单方法是将其导入配置中。请参阅 [使用 Hugo 模块][use-hugo-modules]。

1. 初始化 Hugo 模块系统：`hugo mod init github.com/&lt;your_user&gt;/&lt;your_project&gt;`
2. 导入主题：

   ```toml
   [module]
     [[module.imports]]
       path = &#34;github.com/hugo-fixit/FixIt&#34;
   ```

要更新或管理版本，你可以使用 `hugo mod get` 命令。

```bash
# 更新所有模块
hugo mod get -u
# 更新所有模块及其依赖
hugo mod get -u ./...
# 更新一个模块
hugo mod get -u github.com/hugo-fixit/FixIt
# 获取特定版本（例如 v0.3.2, @latest, @master, @dev）
hugo mod get github.com/hugo-fixit/FixIt@v0.3.2
```

## CLI

FixIt 提供了一个[官方 CLI][fixit-cli]，用于快速搭建 Hugo FixIt 站点骨架。它提供了基于 Git 子模块和 Hugo 模块两种方式来快速搭建 Hugo FixIt 站点，并提供了查看 FixIt 主题最新版本的功能。有关更多详细信息，请参阅 [FixIt CLI 文档][fixit-cli]。

```bash
npm install -g fixit-cli
fixit create my-blog
```

&lt;!-- markdownlint-disable search-replace --&gt;

{{&lt; admonition danger &#34;提醒&#34; &gt;}}
CLI 假定你事先了解 Hugo 和 FixIt。如果你是 Hugo 或 FixIt 的新手，我们强烈建议你在使用 CLI 之前先阅读 [主题文档](../..)，不要使用任何脚手架工具。
{{&lt; /admonition &gt;}}

## 比较

|                          | 手动安装           | Git 克隆           | Git 子模块         | Hugo 模块          |
| ------------------------ | :----------------: | :----------------: | :----------------: | :----------------: |
| 先决条件                 | Hugo               | Hugo, Git          | Hugo, Git          | Hugo, Git, Go      |
| 是否易于安装？           | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| 是否方便升级或降级容易？ | :heavy_check_mark: | :heavy_check_mark: | :white_check_mark: | :white_check_mark: |
| 下载速度如何？           | :x:                | :x:                | :heavy_check_mark: | :white_check_mark: |
| 是否可以自动更新？       | :x:                | :x:                | :white_check_mark: | :white_check_mark: |
| 是否可以使用最新版本？   | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |

&lt;!-- link reference definition --&gt;
[hugo]: https://gohugo.io/
[hugo-install]: https://gohugo.io/installation/
[git]: https://git-scm.com/
[git-install]: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
[go]: https://go.dev/
[go-install]: https://go.dev/doc/install
[dart-sass]: https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass
[dart-sass-install]: https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass
[node.js]: https://nodejs.org/
[node-install]: https://nodejs.org/en/download/
[commit-info]: https://gohugo.io/variables/git/
[cloudcannon]: https://cloudcannon.com/
[cloudflare-pages]: https://pages.cloudflare.com/
[github-pages]: https://pages.github.com/
[gitlab-pages]: https://docs.gitlab.com/ee/user/project/pages/
[netlify]: https://www.netlify.com/
[fixit]: https://github.com/hugo-fixit/FixIt
[fixit-cli]: https://github.com/hugo-fixit/fixit-cli
[releases]: https://github.com/hugo-fixit/FixIt/releases
[git-submodule]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[hugo-modules]: https://gohugo.io/hugo-modules/
[use-hugo-modules]: https://gohugo.io/hugo-modules/use-modules/


---

> 作者: [semifly](https://semifly.top)  
> URL: http://localhost:1313/documentation/installation/  

