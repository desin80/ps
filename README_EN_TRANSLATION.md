# CN_Tutorial_EN_TRANSLATION by desin80

**Preparation**

- MuMu Emulator or other emulators that support root
- [Git](https://git-scm.com/)
- [.NET SDK 8.0](https://dotnet.microsoft.com/en-us/download/visual-studio-sdks)
- [mitmproxy](https://mitmproxy.org/)
- [WireGuard](https://www.wireguard.com/)
- [Private Server](Server.git)
- [Private Server Dependence](Dependence.git)
- Magisk
- Python (run `pip install mitmproxy`)
- BA Japanese Server
- Root Certificate Manager

First, install everything listed above except Magisk and the repositories (install WireGuard and Root Certificate Manager on the emulator). It is recommended to clone the emulator first, as you may need to reinstall the game if it becomes broken.

**Cloning the Repositories**

- Create an empty folder, then open cmd or PowerShell in that folder.
- Enter `git clone [Server.git]` and press Enter.
- Enter `git clone [Private Server Dependence.git]` and press Enter.
- Wait for both to finish cloning before proceeding to the next step.

**Modifying Project Settings**

- Navigate to the `[Private Server Dependence]/Scripts/redirect_server_mitmproxy` folder, open `redirect_server.py`, and change the value of `SERVER_HOST` to the ip you get from running `ipconfig` in cmd (for local use) or your server's IP.
- Right-click `start.cmd` and edit it, replacing "Your IP address" with the same IP. For example: `mitmweb -m wireguard --no-http2 -s redirect_server.py --set termlog_verbosity=warn --ignore 127.0.0.1`.

**Rooting the Emulator with Magisk**

- You can refer to this [tutorial](https://mumu.163.com/help/20240202/35044_1136675.html) to root the emulator with Magisk, then [hide magisk's package name](https://magiskcn.com/hide-the-magisk-app.html). There is no need to hide root or the app list.
- After installing Magisk, install the [cert-fixer module](https://github.com/pwnlogs/cert-fixer) and enable it.
- Open WireGuard, start `start.cmd`, and a webpage will pop up. In WireGuard, click the plus sign and scan the QR code on the webpage.
- After scanning, open the newly added tunnel. Then, in the emulator's browser, go to `mitm.it`, download the certificate for Android, and install it using Root Certificate Manager.
- In Magisk settings, enable Zygisk, MagiskHide, and Enforce SuList, then restart the emulator.

**Starting the Server**

- Navigate to `[Private Server]/[Private Server]`, open cmd or PowerShell, and enter `dotnet run`. After the resources are downloaded, you can enter the server.

**Notes**

- If you cannot access the clan, try modifying the `config.json` and `config.cs` files in the `[Private Server]` folder, changing the IP to the same one used above, and try again.
- the ip in redirect_server.py, start.cmd, config.json, config.cs(found in [Private Server]/[Private Server]/Utils folder) must be the same.
