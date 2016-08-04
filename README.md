# 介绍
## icodesign
该文件夹是 Potato 最新版，由 [icodesign][1] 维护，不定期更新。
[https://github.com/shadowsocks/Potatso]() 

## liruqi
该文件夹是另一个作者维护的 Potatso， Build 版本不一定是最新版。
[https://github.com/liruqi/Potatso-iOS]()

## Other
该文件夹包含 [shadowsocks-iOS][4]，[shadowsocks-libev][5] 和 Potato 的 Podfile 修改后的文件。


# 构建方式
## 框架依赖
- [Potatso 官方配置说明][6]

- [Issues 中发布的构建步骤][7]

- [shadowsocks-libev 时发生错误解决方式][8]

---- 

如果在执行  `git submodule update --init` 时发生错误，需要手动下载 [shadowsocks-libev][9] （或者在 shadowsocks-libev 文件夹下获取旧版本），复制到 

	/Potatso/Library/ShadowPath/ShadowPath/shadowsocks-libev 

文件夹目录下，然后在 Terminal 中进入该文件夹，执行 

	./configure --with-openssl="{user path}/ShadowPath/ShadowPath/libopenssl"

编译 shadowsocks-libev 下的文件。

复制 `/Potatso/Other/CocoaPod-Podfile/` 下 `Podfile` 文件到 `/Potatso` 项目的根目录下，执行 

	pod install

再通过 Terminal 执行
 
	carthage update

编译 

	/Potatso/Carthage/Checkouts/YAML.framework/YAML.xcodeproj

## 项目编译
修改 Targets -\> Identity -\> Team 

	X-Reception Technology (Beijing) Co., Ltd.

修改项目 Targets -\> Bundle Identifier

	Potatso: com.zuiqt.potatso
	PacketTunnel: com.zuiqt.potatso.PacketTunnel
	TodayWidget: com.zuiqt.potatso.TodayWidget 

关闭 `Capabilites` 中的 `Push Notification` 和 `Background Modes`,

去掉三个 Target 的 App Group 原来的钩，并选择 

	group.com.zuiqt.duotaidemo 

之后修改 `PacketTunnel/PacketTunnelProvider.m` 中 `initWithApplicationGroupIdentifier` 的 `identifier` 为

	group.com.zuiqt.duotaidemo 

三个 Targets 的 Provisioning Profile 均在[开发者平台][10]建好，如状态为 `Invalid`，重新 “Edit -\> Generate” 即可重新激活。

之后即可在编译执行。 






[1]:	https://github.com/icodesign
[4]:	https://github.com/liruqi/shadowsocks-iOS
[5]:	https://github.com/shadowsocks/shadowsocks-libev
[6]:	https://github.com/shadowsocks/Potatso/wiki/Setup-Guide
[7]:	https://github.com/shadowsocks/Potatso/issues/12
[8]:	https://github.com/shadowsocks/Potatso/issues/46
[9]:	https://github.com/shadowsocks/shadowsocks-libev
[10]:	https://developer.apple.com/account/ios/profile/