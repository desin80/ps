# CN_Tutorial by desin80

[EN_TRANSLATION](README_EN_TRANSLATION.md)

**准备**

- MuMu 模拟器或者其他支持 root 的模拟器
- [Git](https://git-scm.com/)
- [.NET SDK 8.0](https://dotnet.microsoft.com/en-us/download/visual-studio-sdks)
- [mitmproxy](https://mitmproxy.org/)
- [WireGuard](https://www.wireguard.com/)
- [Private Server](Server.git)
- [Private Server Dependence](Dependence.git)
- Magisk
- Python(运行 pip install mitmproxy)
- BA 日服
- Root Certificate Manager
  先把上面除了 Magisk 和仓库都安装好(WireGuard 和 Root Certificate Manager 安装到模拟器上)，建议先克隆一下模拟器，不然游戏进不去了可能要重装

**克隆仓库**

- 创建一个空文件夹，在里面 shift+右键打开 cmd 或者 powershell
- 输入`git clone [Server.git]`然后回车
- 输入`git clone [Private Server Dependence.git]`然后回车
- 等待都克隆好进行下一步

**修改项目设置**

- 进入[Private Server Dependence]/Scripts/redirect_server_mitmproxy 文件夹, 打开 redirect_server.py，把 SERVER_HOST 的值改成 cmd运行`ipconfig` 获取的ip 或者你的服务器 ip
- 右键`start.cmd`，编辑,把 Your IP address 改成同样的 ip，比如`mitmweb -m wireguard --no-http2 -s redirect_server.py --set termlog_verbosity=warn --ignore 127.0.0.1`

**模拟器刷面具**

- 可以参考这篇[教程](https://mumu.163.com/help/20240202/35044_1136675.html)先刷好面具，然后[隐藏包名](https://magiskcn.com/hide-the-magisk-app.html)，不用隐藏 root 和应用列表
- Magisk 刷好之后安装[cert-fixer 模块](https://github.com/pwnlogs/cert-fixer)，记得启用
- 打开 WireGuard，启动 start.cmd，会弹出来一个网页，然后在 WireGuard 里点加号，扫弹出来的网页（Capture 那一栏）的二维码
- 扫完之后打开刚添加的隧道，然后模拟器的浏览器输入`mitm.it`，找到安卓端的证书下载，然后再用 Root Certificate Manager 安装刚下载的证书
- 在 Magisk 设置里打开 Zygisk、MagiskHide、实现 SuList 然后重启模拟器

**启动服务器**

- 进入[Private Server]/[Private Server]，在里面 shift+右键打开 cmd 或者 powershell，输入`dotnet run`，下载完资源就可以进服了

**注意事项**

- 如果进不去社团可以尝试修改[Private Server]文件夹里的 config.json 和 config.cs（自己找一找），把里面的 ip 改成和上面一样的 ip 再试试
- 最后redirect_server.py, start.cmd, config.json, config.cs里的ip一定要一样
