# [Action-OpenWrt-Rpi](https://github.com/SuLingGG/Action-OpenWrt-Rpi)

## 写在前面

本项目基于 P3TERX 的 Actions-OpenWrt 项目:

<https://github.com/P3TERX/Actions-OpenWrt>

本项目还参考了以下项目的部分代码:

<https://github.com/project-openwrt/The-Compiled-OpenWrt-Firmwares>

<https://github.com/ljk4160/GDOCK>

特此感谢~

## 功能实现

此项目基于 Github Action 平台，可实现以下功能:

- 自动搭建 OpenWrt 编译环境
- 自动拉取 OpenWrt 代码及一些优秀的第三方软件包项目
- 自动构建适用于树莓派各版本的 OpenWrt 固件
- 固件构建完毕后自动发布相应 Action 任务首页以供下载

## 使用方法

1. 在 Github 中 Fork Action-OpenWrt-Rpi 仓库至你的账户下。

2. 复制 template/config 文件夹中所编译 "设备-版本" 的 config 文件至 `项目根目录`。

   复制 template/workflows 文件夹中所编译 "设备-版本" 的 yml 文件至 `.github/workflows` 目录。

   同时，项目已预置适用于树莓派 2~4 的 Lean 大版 OpenWrt 配置文件，可开箱即用。

   以下步骤任选其一即可:

   (以 config 文件为例，yml 文件同理)

   (1) 使用 git 命令:
   
   git clone 你 **Fork 后的项目** 到本地，将所需 config 文件从 template 目录中复制到项目根目录，然后 git add & git commit & git push。
   
   (如果你不熟悉 git 命令，不建议采用此方法)
   
   (2) 在 Github 桌面版网页中在线操作:
   
   在 Github 仓库中的 template 文件夹找到你想要编译的 config 文件，全选文件内容并复制，接着回到项目根目录，新建一个文件，粘贴刚刚复制的内容，同时此文件的文件名需确保与 template 文件夹中的相应文件名 **完全一致** 。完成以上步骤后提交即可。

完成以上两步后，Github Action 即可自动开始编译。

## 触发方式

本项目采用两种触发方式:

1. 检测到项目根目录下指定文件名.config 文件发生变动(下文说明)

2. 新的 Release 被发布

此外，Github Action 支持多种触发方式，比如定时触发、Star 触发等，详细操作方法请前往 [P3terx 大佬的博客](https://p3terx.com/archives/build-openwrt-with-github-actions.html) 中查看~

## 关于配置文件

1. 本项目提供的配置文件与博客中 "[自编译 OpenWrt 固件](https://mlapp.cn/369.html)" 功能基本相同。

2. 配置文件涵盖树莓派 1\~4 四个设备，每个设备又分为官方版 OpenWrt 与 Lean 大版 OpenWrt 两个配置文件，其中适用于树莓派 2 的配置文件通用于树莓派 2\~4，除此之外的其他配置文件互不通用。

3. 建议直接编辑配置文件增删固件功能，编辑配置文件时只需要增删最顶层的软件包即可，软件包依赖项可不必在配置文件中体现。

## 注意事项

1. 在不更改 Github Action 描述文件 ( /github/workflows/yml 文件) 的情况下，项目根目录下 config 文件名须与 template 文件夹下的文件名完全一致。若文件名有出入则不会触发自动编译。

2. 因 Github Action 限制，编译后生成的固件及相关文件需要登录 Github 帐号方可查看及下载。

3. 因 Github Action 限制，提供下载的文件均为压缩后的 zip 文件，故文件实际下载大小与页面所示大小不符，文件解压后应与页面标识大小相符。

4. **强烈建议只编译所需固件以节约公共计算资源**。
