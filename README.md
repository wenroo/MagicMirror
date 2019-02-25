![MagicMirror²: 模块化开源智能镜软件解决方案。 ](.github/header.png)

<p align="center">
	<a href="https://david-dm.org/MichMich/MagicMirror"><img src="https://david-dm.org/MichMich/MagicMirror.svg" alt="Dependency Status"></a>
	<a href="https://david-dm.org/MichMich/MagicMirror#info=devDependencies"><img src="https://david-dm.org/MichMich/MagicMirror/dev-status.svg" alt="devDependency Status"></a>
	<a href="https://bestpractices.coreinfrastructure.org/projects/347"><img src="https://bestpractices.coreinfrastructure.org/projects/347/badge"></a>
	<a href="http://choosealicense.com/licenses/mit"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License"></a>
	<a href="https://travis-ci.org/MichMich/MagicMirror"><img src="https://travis-ci.org/MichMich/MagicMirror.svg" alt="Travis"></a>
	<a href="https://snyk.io/test/github/MichMich/MagicMirror"><img src="https://snyk.io/test/github/MichMich/MagicMirror/badge.svg" alt="Known Vulnerabilities" data-canonical-src="https://snyk.io/test/github/MichMich/MagicMirror" style="max-width:100%;"></a>
	<a href="http://slack.magicmirror.builders"><img src="http://slack.magicmirror.builders:3000/badge.svg" alt="Slack Status"></a>
</p>

## 修改记录

- 翻译README文档（持续...）
  - 根目录README文档(DONE)
- 模块的使用和翻译（持续...）
- 发现的问题（持续...）

## 源文档

[源文档](https://github.com/MichMich/MagicMirror)

**MagicMirror²** 是一款开源的，支持模块化的智能镜软件解决方案。可以安装各种扩展模块，**MagicMirror²** 会将您的过道镜子，浴室镜子，换衣间镜子变成您的私人助理。**MagicMirror²** 项目是由[创始人](http://michaelteeuw.nl/tagged/magicmirror)和原来越多的[贡献者](https://github.com/MichMich/MagicMirror/graphs/contributors)一起发展起来的。

MagicMirror² 是一个致力于模块化开发的系统, 它使用[Electron](http://electron.atom.io/) 作为软件平台.所以并不需要安装其他的WEB服务器程序，也不需要另外使用浏览器访问。

## 目录

- [安装](#安装)
  - [树莓派](#树莓派-raspberry-pi)
  - [通用设置](#通用设置)
  - [只运行服务器程序](#只运行服务器程序)
  - [只运行客户端程序](#只运行客户端程序)
  - [Docker](#docker)
- [设置](#设置)
- [模块](#模块)
- [更新](#更新)
- [反馈](#known-issues)
- [社区](#社区)
- [教程](#教程)
- [宣言](#宣言)

## 安装

### 树莓派 Raspberry Pi

#### 智能安装 (!仅限于树莓派)

*Electron* 是用来封装MagicMirror²的程序, 只支持树莓派Pi2/Pi3的版本. 树莓派Pi0/Pi1当前还 **不能** 支持. 如果想在版本P1的树莓派上运行,请选用[只运行服务器程序](#只运行服务器程序) 用来在一个全屏的浏览器上运行。(当然, 也有人研究出了在树莓派Pi0上运行的方法，如果你坚持请去论坛搜索。)

注意：需要安装Raspbian的最新完整版本，**不要使用Lite版本**。
Note that you will need to install the latest full version of Raspbian, **don't use the Lite version**.

在树莓派上执行以下命令来安装MagicMirror²:

```bash
bash -c "$(curl -sL https://raw.githubusercontent.com/MichMich/MagicMirror/master/installers/raspberry.sh)"
```

#### 手动安装

1. 下载和安装最新的 *Node.js* 版本:
- `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
- `sudo apt install -y nodejs`
2. 克隆版本库并切换到master分支: `git clone https://github.com/MichMich/MagicMirror`
3. 进入文件夹: `cd MagicMirror/`
4. 安装程序的依赖并运行: `npm install && npm start` \
   如果您选择的是 **只运行服务器程序** ,那么请运行: `npm install && node serveronly` .


**:注意: 非常重要!**

- **执行安装依赖程序 `npm install` 会需要比较长的时间**, 会有极小的可能出现程序无法响应的情况! \
  如果您使用的是树莓派Pi3的版本，大约需要 **~10** 分钟，如果使用的是树莓派pi2笨笨 **~25** 分钟. \
  PS: 国内一般时间更长的情况也很多 \
  不要中断操作，不然有可能会出现 broken_heart：Raspberry Jam。


还需要注意:
- `npm start`不能**通过SSH工作。但你可以使用`DISPLAY =：0 nohup npm start＆`代替。 \
  这将启动远程显示器上的镜像。
 - 如果你想在Raspberry Pi上进行调试，可以使用`npm start dev`，它将在启用* Dev Tools *的情况下启动MM。
 - 要在镜像模式下访问工具栏菜单，请按“ALT”键。
 - 要从镜像模式切换（web）`Developer Tools`，使用`CTRL-SHIFT-I`或`ALT`并选择`View`。

- 如果 `npm start`  **不能** 在SSH上运行. 那么你可以使用 `DISPLAY=:0 nohup npm start &`， \
  这个会进入镜像模式，启用远程显示器上的镜像。
- 如果你想进入调试模式或者开发模式在树莓派上，可以使用命令 `npm start dev` ，这个会启动 *Dev Tools* .
- 如果你想在镜像模式下访问工具栏，请按 `ALT` 键.
- 如果你想在镜像模式下切换 (web) `Developer Tools` , 可以按键 `CTRL-SHIFT-I` 或者 按住 `ALT` 并选择 `View`.


### 只运行服务器程序

有些时候，你可能需要在另外一个窗口或者显示设备上看到输出结果，这里只需要运行程序和服务。在这种情况下，你可以运行 `node serveronly`  进入 MagicMirror² 的服务器程序（server only） 模式,使用Docker情况下也需要这样，这个会启动服务程序，然后你可以在其他你需要输出的设备上的浏览器里输出显示结果。

**非常重要:** 需要将服务器配置中的 interface/ip (`ipWhitelist`) 放入白名单，以便于客户端来连接他，否则将不能连接到服务器。同时还需要将树莓派的本地主机的HOST `address` 设置为 `0.0.0.0` ，这样会监听所有的接口，否则 `localhost` (default)只会监听本机。

```javascript
var config = {
	address: "0.0.0.0",	// default is "localhost"
	port: 8080,		// default
	ipWhitelist: ["127.0.0.1", "::ffff:127.0.0.1", "::1", "::ffff:172.17.0.1"], // default -- need to add your IP here
	...
};
```


### 只运行客户端程序

当你准备好了一台运行中的服务器，并希望树莓派可以连接过去并显示你的输出界面。 \
请执行: `node clientonly --address 192.168.1.5 --port 8080`. (配置你指定的IP地址和端口号)


### Docker

MagicMirror² 可以使用 [Docker](https://docker.com) 来部署只运行服务器程序模式，当你成功[安装Docker](https://docs.docker.com/engine/installation/) 后，只需要在shell中执行以下命令:

```bash
docker run  -d \
	--publish 80:8080 \
	--restart always \
	--volume ~/magic_mirror/config:/opt/magic_mirror/config \
	--volume ~/magic_mirror/modules:/opt/magic_mirror/modules \
	--name magic_mirror \
	bastilimbach/docker-magicmirror
```
如果你想得到更多关于 Dockerfile 的版本和配置信息，请浏览[GitHub版本库](https://github.com/bastilimbach/docker-MagicMirror).


## 设置

### 树莓派的设置

以下的百科地址会帮助你进行关于 MagicMirror² 运行在系统上的初始设置:
- [设置树莓派](https://github.com/MichMich/MagicMirror/wiki/Configuring-the-Raspberry-Pi)
- [自动运行MagicMirror](https://github.com/MichMich/MagicMirror/wiki/Auto-Starting-MagicMirror)


### 通用设置

1. 拷贝(`cp`) `/home/pi/MagicMirror/config/config.js.sample` 到 `/home/pi/MagicMirror/config/config.js`. \
   **注意:** 如果你是使用脚本安装的，那么这个步奏已经完成

2. 进行必须的依赖配置. \
   注意: 你可以运行命令 `npm run config:check` 在 `/home/pi/MagicMirror` 上来检查你的配置。


可以配置的属性和参数:

| **配置项** | **备注** |
| --- | --- |
| `port` | 运行 MagicMirror² 服务的端口. 默认值为 `8080`. |
| `address` | 接受连接的 *interface* IP地址. 默认值为 `localhost`, 这会阻止本机的web服务器暴露给局域网内的其他计算机. 如果要开放连接，请使用: `0.0.0.0`. |
| `ipWhitelist` | 允许连接到 MagicMirror² 的IP地址列表. 默认值为 `["127.0.0.1", "::ffff:127.0.0.1", "::1"]`, 只允许 `localhost` 本机）. 请添加你需要的地址. 这里还可以使用子网掩码 (`["127.0.0.1", "127.0.0.1/24"]`) ，或者直接使用 (`["127.0.0.1", ["192.168.0.1", "192.168.0.100"]]`)指定IP的范围. 在 `[]` 里输入所有允许的地址. 更多的信息请参考: [follow post ipWhitelist HowTo](https://forum.magicmirror.builders/topic/1326/ipwhitelist-howto) |
| `zoom` | 可以指定镜像显示的缩放. 默认值为 `1.0`|
| `language` | 界面语言。 (注意:不是所有元素都会被本地化) 可选值为 `en`, `nl`, `ru`, `fr` 等等。默认值为 `en`。 |
| `timeFormat` | 时间的输出模式. 可选值为 `12` or `24`. 默认值为 `24`。 |
| `units` | 设置天气模块的单位. 可选值为 `metric` or `imperial`（公制/英制）. 默认值为 `metric`。 |
| `modules` | 一组当前的模块。 **数组里面必须包含对象. 详情请看下面的表格** |
| `electronOptions` | Electron (浏览器) 的选项和配置. 这里可以配置比如浏览器的大小和位置 (例: `electronOptions: { fullscreen: false, width: 800, height: 600 }`). Kiosk模式可以通过配置 `kiosk: true` 打开，还有就是 `autoHideMenuBar: false` 和 `fullscreen: false` 等等配置。更多配置信息请参考[这里](https://github.com/electron/electron/blob/master/docs/api/browser-window.md). |
| `customCss` | 个性化样式文件 `custom.css` 的地址. 默认值为 `css/custom.css`. |


| **配置项** | **备注** |
| --- | --- |
| `module` | 模块名. 这里可以包含子文件夹. 比如加入 `clock`, `default/calendar` 和 `custommodules/mymodule`. |
| `position` | 模块会在终端显示的位置. 可以设置如 `top_bar`, `top_left`, `top_center`, `top_right`, `upper_third`, `middle_center`, `lower_third`, `bottom_left`, `bottom_center`, `bottom_right`, `bottom_bar`, `fullscreen_above`, and `fullscreen_below`。 这个配置为 *可选项* ，但是大多数模块是需要设置的，模块的文档里面会有更多的信息。模块的显示顺序会依照文件里面的输入顺序，可以调整文件里的模块顺序进行排序。 |
| `classes` | 给模块传递其它的类. *可选项* |
| `header` | 如果需要在头部显示文本内容，请添加内容的属性。*可选项* |
| `disabled` | 设置这个值为 `true` 调过创建中的模块. *可选项* |
| `config` | 模块的配置属性。 更多信息请查看模块的文档。除非这个模块需要一些额外的配置，一般情况下这里为*可选项* |

## 模块

默认安装的模块：

- [**Clock** /时钟](modules/default/clock)
- [**Calendar** /日历](modules/default/calendar)
- [**Current Weather** /当前天气](modules/default/currentweather)
- [**Weather Forecast** /天气预报](modules/default/weatherforecast)
- [**News Feed** /新闻订阅](modules/default/newsfeed)
- [**Compliments** /赞美词](modules/default/compliments)
- [**Hello World** /欢迎词](modules/default/helloworld)
- [**Alert** /警告](modules/default/alert)

更多的模块请点击 [MagicMirror² 第三方模块](https://github.com/MichMich/MagicMirror/wiki/3rd-party-modules). 如果你想创建自己的模块, 请查看 [MagicMirror² 模块开发文档](modules) ，同时请不要忘记将其加入到WIKI和[论坛](https://forum.magicmirror.builders/category/7/showcase)!


## 更新

如果你想要更新 MagicMirror² 到最新版本, 请在你的 Magic Mirror文件夹目录运行命令:

```bash
git pull && npm install
```

如果你只更改了配置和模块，更新一般没有什么问题。
输入命令 `git status` 来检查你的修改, 如果这里显示有修改, 你可以使用恢复命令 `git reset --hard` 进行重置。然后在运行 `git pull` 更新。


## 社区

MagicMirror² 的社区正在不断的壮大中。我们的[论坛](https://forum.magicmirror.builders) 里可以让你分享创意，提出疑问, 帮助其他人和获得启发，我们在这里等你！

## 教程

欢迎各种贡献，不仅仅是代码，还有文档和错误报告。

请关注一下几点:

- **错误报告**: 确保你运行的是最新版本，如果错误依然存在，请明确你的标题提出明确的问题。
- **小错误修复**: 请发送拉取请求并清楚的解释问题或者给出解决问题的连接。
- **主要错误修复**: 请先在GitHub的问题中讨论你的方法，如果有必要，然后再去修改大部分的代码。
- **新功能**: 请先在GitHub的问题中讨论你的方法，如果有必要，然后再去修改大部分的代码。如果没有讨论，拉取的请求将不会被接受合并。

谢谢你的帮助，我们会将 MagicMirror² 做得更好!

## 宣言

持续的在写宣言。直到迈克尔回答了[一个问题]（https://github.com/MichMich/MagicMirror/issues/1174），并给了个很棒的总结：

> "... 我最终将这个项目作为树莓派爱好者的启动项目，事实上，对于大部分贡献者来说，MagicMirror 项目也是他们参与的第一个开源项目。 这就是为什么MagicMirror 项目在几个树莓派杂志中出现的原因。
>
> 项目有很多可以改进的地方。我们能像VUE框架那样提升你的开发速度；我们也能想SASS对于CSS的改变那样给你带来更好，更简单的体验；我们甚至可以把它当成NPM安装工具包那样。就像你说的，我们把这个捆绑起来。最大的缺点就是在改变过程中会变得越来越复杂，用户不能只打开一个文件来进行一个很小的修改，也不能简单的理解是如何工作的。
>
>当然,捆绑的版本可以补充非捆绑版本的缺失，我相信很多的（新）用户将会去选择捆绑版本。但是这些用户并不会去做一些原理的研究和探索，他们只是“使用者”。他们不会变成贡献者，更糟的是：他们连软件开发的尝试都不回去想。
>
>实话实说: 鼓励这些用户去迈出舒适的使用者的那一步是我开发这个项目的动力，所以，我会劲量的持续开发这个项目。
>
> ~ Michael Teeuw


<p align="center">
<br>
	<a href="https://forum.magicmirror.builders/topic/728/magicmirror-is-voted-number-1-in-the-magpi-top-50"><img src="https://magicmirror.builders/img/magpi-best-watermark-custom.png" width="150" alt="MagPi Top 50"></a>
</p>
