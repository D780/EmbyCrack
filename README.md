# EmbyCrack
[English Version](https://github.com/YukiCoco/EmbyCrack/blob/master/README-EN.md)
## Feature
+ 破解 Emby 高级版验证
+ 修改了默认插件源，加速中国用户下载插件
+ docker 一键安装

## Usage

### 服务端
#### 手动替换
+ **注意**：如果以前使用其他破解方案，必须将系统的 hosts 的 `mb3admin.com` `www.mb3admin.com` 条目删除，否则破解不会生效
+ 将 [破解程序集](https://github.com/YukiCoco/EmbyCrack/tree/master/assembly) 替换原有文件即完成破解，原有文件路径为 `system/System.Net.Http.dll`

#### 使用 Docker
+ `yukinococo/emby_crack:unix-x64`（Unix）
+ `yukinococo/emby_crack:windows-x64` （Windows）

### 客户端
+ 浏览器：安装 [URLRedirector]() 插件，将 `https://mb3admin.com` 替换为 `http://crackemby.neko.re`
+ Android & Android TV：直接使用破解版，自己找找就有了


+ 详细使用方法移步[这里](https://neko.re/archives/128.html)

### 服务端破解
+注意：如果以前使用其他破解方案，必须将系统的 hosts 的 mb3admin.com www.mb3admin.com 条目删除，否则破解不会生效

+简要方法：只需要将 破解程序集 替换原有文件即完成破解，原有文件地址为 system/System.Net.Http.dll，或使用 docker 直接安装破解版。

### 具体方法：

Linux : systemctl stop emby-server.service 结束 emby 进程，ps -aux | grep "emby" 找到 emby 我的 emby 所在目录为（见下文） /opt/emby-server/system/，使用 wget -O /opt/emby-server/system/System.Net.Http.dll 'https://github.com/YukiCoco/EmbyCrack/raw/master/assembly/unix-x64/System.Net.Http.dll' --no-check-certificate 下载破解程序集替换原有程序，然后启动 Emby 进程 systemctl start emby-server.service
yukino@yukino-AA-B4:~$ ps -aux | grep "emby"
root      382423  2.3  1.8 4377788 148512 ?      Ssl  02:33   0:15 /opt/emby-server/system/EmbyServer -programdata /var/lib/emby -ffdetect /opt/emby-server/bin/ffdetect -ffmpeg /opt/emby-server/bin/ffmpeg -ffprobe /opt/emby-server/bin/ffprobe -restartexitcode 3 -updatepackage emby-server-deb_{version}_amd64.deb
Windows：下载后替换即可。
Docker：docker ps 得到 emby docker 的 CONTAINER ID ，然后输入 docker exec -it $CONTAINER ID /bin/sh 进入 docker 终端，wget https://github.com/YukiCoco/EmbyCrack/raw/master/assembly/unix-x64/System.Net.Http.dll 下载 dll，然后 cp System.Net.Http.dll system/ 替换原有 dll ，然后重启 emby docker 即可。
Docker：你也可以直接安装破解版本的 Emby Docker，安装镜像使用
yukinococo/emby_crack:unix-x64 （Unix）, yukinococo/emby_crack:windows-x64 （Windows）
至此，服务端破解就已经生效了，接下来还需要在浏览器做一些小修改才能在 PC 上完全使用，坐和放宽 :）

### 客户端破解
注意：如果以前使用其他破解方案，必须将系统的 hosts 的 mb3admin.com www.mb3admin.com 条目删除，否则破解不会生效

PC 浏览器：安装 URLRedirector https://chrome.google.com/webstore/detail/urlredirector/maolmdhneopinciaokgohljhpdedekee 插件，添加用户规则
原始地址 https://mb3admin.com ，目标地址 http://crackemby.neko.re ，然后确认并保存，别忘了勾选重定向。
![emby1-1024x623.png](https://neko.re/wp-content/uploads/2020/07/emby1-1024x623.png)
![emby2.png](https://neko.re/wp-content/uploads/2020/07/emby2.png)
输入任意字符后这样显示，就是破解完成了。
![QQ20200724-105359-1024x650.png](https://neko.re/wp-content/uploads/2020/07/QQ20200724-105359-1024x650.png)
Android & TV：使用 Emby 破解版本
至此，破解工作全部结束，Enjoy~

高级应用
服务端获取插件源已经替换为我的，但是后台显示插件图片采用的是 https://raw.githubusercontent.com 这个节点，国内访问速度很慢，建议加入到自己的代理白名单。
