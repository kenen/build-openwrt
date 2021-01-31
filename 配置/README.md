lede 编译配置
Target Images  --->  ext4（可读写文件系统，不支持恢复出厂设置，软件包可完全卸载）
Target Images ---> (256) Kernel partition size (in MB)                        #默认是 (16) 
              ---> (512) Root filesystem partition size (in MB)        #默认是 (160) 
Base system ---> blockd 
Administration ---> netdata(实时监控)
Extra packages ---> autosamba(只支持samba3,选择samba4时去掉)
               --->  ipv6helper  （支持 iPv6：选定这个后下面几项自动选择了）
      Network  --->  odhcp6c
      Network  --->  odhcpd-ipv6only
      LuCI  --->  Protocols  --->  luci-proto-ipv6
      LuCI  --->  Protocols  --->  luci-proto-ppp
Kernel modules ---> Block Devices（块设备支持） ---> kmod-ata-core（串行ATA总线支持，即SATA硬盘支持) ---> kmod-ata-ahci 
                                               ---> kmod-block2mtd
                                               ---> kmod-scsi-generic（usb转IDE,SATA) 
               ---> Filesystems（文件系统支持） ---> kmod-fs-nfs
                                               ---> kmod-fs-nfs-common
               ---> Native Language Support (语言编码支持) ---> kmod-nls-cp936 (中文字符支持)
               ---> Network Devices (有线网卡支持)---> 按需选择
               ---> USB Support（USB设备支持） ---> kmod-usb-ohci
                                              ---> kmod-usb-storage
                                              ---> kmod-usb-storage-extras
                                              ---> kmod-usb-storage-uas
                                              ---> kmod-usb-uhci(usb1.1驱动)
                                              ---> kmod-usb2
                                              ---> kmod-usb3
               ---> Virtualization（虚拟化） ---> kmod-kvm-intel (intel处理器)
                                            ---> kmod-kvm-x86
               ---> Wireless Drivers（无线网卡选择）---> 按需选择
LuCI  --->  Application  ---> luci-app-accesscontrol  #访问时间控制
                         ---> luci-app-adbyby-plus  #广告屏蔽大师Plus +
                         ---> luci-app-adguardhome  #AdGuard home广告过滤（Li大内插件）
                         ---> luci-app-advanced #高级设置
                         ---> luci-app-advanced-reboot  #Linksys高级重启
                         ---> luci-app-advancedsetting  #系统高级设置（Li大内插件）
                         ---> luci-app-ahcp  #Ad-Hoc配置协议(AHCP) ipv6 and 双栈 自动配置协议 !
                         ---> luci-app-airplay2   #Apple AirPlay2 无损音频接收服务器
                         ---> luci-app-amule  #aMule下载工具 !
                         ---> luci-app-argon-config     #argon主题设置
                         ---> luci-app-aria2 # Aria2下载工具
                         ---> luci-app-arpbind  #IP/MAC绑定
                         ---> luci-app-autoreboot  #支持计划重启
                         ---> luci-app-baidupcs-web  #百度网盘管理
                         ---> luci-app-bird1-ipv4  #对Bird1-ipv4的支持
                         ---> luci-app-bird1-ipv6  #对Bird1-ipv6的支持
                         ---> luci-app-control-timewol     #网络唤醒
                         ---> luci-app-control-webrestriction     #访问限制
                         ---> luci-app-control-weburl     #网址过滤
                         ---> luci-app-cpulimit     #cpu使用率限制工具
                         ---> luci-app-ddns   #动态域名 DNS（集成阿里DDNS客户端）
                         ---> luci-app-diskman   #磁盘管理工具
                                  luci-app-diskman ---> Include btrfs-progs   #新型的写时复制 (COW)
                                  luci-app-diskman ---> Include lsblk   #lsblk命令 用于列出所有可用块设备的信息
                                  luci-app-diskman ---> Include mdadm   #mdadm命令 用于创建、管理、监控RAID设备的工具   
                         ---> luci-app-dnscrypt-proxy  #DNSCrypt解决DNS污染
                         ---> luci-app-dnsforwarder  #DNSForwarder防DNS污染
                         ---> luci-app-docker  #dockerman容器
                         ---> luci-app-e2guardian   #Web内容过滤器
                         ---> luci-app-eqos  #依IP地址限速（Li大内插件）
                         ---> luci-app-familycloud   #家庭云盘
                         ---> luci-app-filetransfer  #文件传输（可web安装ipk包）
                         ---> luci-app-firewall   #添加防火墙
                         ---> luci-app-flowoffload  #Turbo ACC网络加速（集成FLOW,BBR,NAT,DNS...
                         ---> luci-app-frpc   #内网穿透Frp客户端
                         ---> luci-app-frps   #内网穿透Frp服务端
                         ---> luci-app-fwknopd  #Firewall Knock Operator服务器
                         ---> luci-app-gost  #隐蔽的https代理（Li大内插件）
                         ---> luci-app-gowebdav     #GoWebDav 是一个轻巧、简单、快速的 WebDav 服务端程序
                         ---> luci-app-guest-wifi   #WiFi访客网络
                         ---> luci-app-haproxy-tcp   #HAProxy负载均衡-TCP
                         ---> luci-app-hd-idle  #硬盘休眠
                         ---> luci-app-hnet  #Homenet Status家庭网络控制协议
                         ---> luci-app-https-dns-proxy  #通过HTTPS代理为DNS提供Web UI
                         ---> luci-app-ipsec-virtual**d  #virtual**服务器 IPSec
                         ---> luci-app-jd-dailybonus  #京东签到服务   *
                         ---> luci-app-kodexplorer  #KOD可道云私人网盘（与vnStat冲突 ! ）
                         ---> luci-app-koolproxyr  #KP去广告
                         ---> luci-app-lxc   #LXC容器管理
                         ---> luci-app-mentohust     #MentoHUST 的 LuCI 控制界面
                         ---> luci-app-meshwizard #网络设置向导
                         ---> luci-app-music-remote-center   #PCHiFi 数字转盘遥控
                         ---> luci-app-mwan3   #MWAN3负载均衡
                         ---> luci-app-mwan3helper   #MWAN3分流助手
                         ---> luci-app-n2n_v2   #N2N内网穿透 N2N v2 virtual**服务
                         ---> luci-app-netdata  #Netdata实时监控（图形化）
                         ---> luci-app-nfs   #NFS网络共享
                         ---> luci-app-nft-qos  #QOS流控 Nftables版
                         ---> luci-app-nlbwmon   #网络带宽监视器
                         ---> luci-app-noddos  #NodDOS Clients 阻止DDoS攻击
                         ---> luci-app-nps   #内网穿透nps
                         ---> luci-app-ntpc   #NTP时间同步服务器
                         ---> luci-app-oaf  #应用过滤
                         ---> luci-app-openclash  #OpenClash代理客户端（Li大内插件）
                         ---> luci-app-openvpn
                         ---> luci-app-openvpn-server 
                         ---> luci-app-pagekitec   #Pagekitec内网穿透客户端
                         ---> luci-app-打倒美帝  #打倒美帝（Li大内插件）
                                  Configuration ---> Include 违禁软件  #SS代理
                                  Configuration ---> Include 违禁软件 Server  #SS服务器
                                  Configuration ---> Include 违禁软件R   #违禁软件代理
                                  Configuration ---> Include 违禁软件R Server  #违禁软件服务器
                                  Configuration ---> Include Xray  #Xray代理
                                  Configuration ---> Include 违禁软件  #违禁软件代理
                                  Configuration ---> Include Trojan_Plus  #Trojan_Plus代理
                                  Configuration ---> Include Trojan_GO  #Trojan_GO代理
                                  Configuration ---> Include Brook  #Brook代理
                                  Configuration ---> Include NaiveProxy  #NaiveProxy代理
                                  Configuration ---> Include Kcptun  #Kcptun加速
                                  Configuration ---> Include haproxy  #HAProxy  #HAProxy负载均衡
                                  Configuration ---> Include china-dns-NG  #防污染DNS服务
                                  Configuration ---> Include Https DNS Proxy(DoH)  #HttpsDNS服务（丢弃）
                                  Configuration ---> Include dns2socks  #DNS服务器
                                  Configuration ---> Include 违禁软件-plugin (违禁软件 plugin)  #SS 违禁软件插件
                                  Configuration ---> Include simple-obfs (违禁软件 plugin)  #simple-obfs简单混淆工具
                         ---> luci-app-polipo  #Polipo代理(是一个小型且快速的网页缓存代理)
                         ---> luci-app-poweroff     #关机（增加关机功能
                         ---> luci-app-pptp-vpnserver-manyusers     #PPTP VPN 服务器
                         ---> luci-app-privoxy  #Privoxy网络代理(带过滤无缓存)
                         ---> luci-app-ps3netsrv  #PS3 NET服务器（用于加载蓝光/游戏ISO/PKG）
                         ---> luci-app-qbittorrent  #BT下载工具（qBittorrent）
                         ---> luci-app-qos   #流量服务质量(QoS)流控
                         ---> luci-app-ramfree  #释放内存
                                  Include rclone-webui  #Rclone界面
                                  Include rclone-ng (another webui)  #Rclone另一个界面
                                  Include fuse-utils (mount cloud storage)  #fuse-utils（挂载云存储）
                         ---> luci-app-rp-pppoe-server  #Roaring Penguin PPPoE Server 服务器
                         ---> luci-app-samba   #网络共享（Samba）
                         ---> luci-app-samba4   #网络共享（Samba4）
                         ---> luci-app-sfe  #Turbo ACC网络加速（flowoffload二选一）
                         ---> luci-app-违禁软件   #SS打倒美帝
                         ---> luci-app-违禁软件-libes  #SS-libev服务端
                         ---> luci-app-shairplay  #支持AirPlay功能
                         ---> luci-app-siitwizard  #SIIT配置向导  SIIT-Wizzard
                         ---> luci-app-simple-adblock  #简单的广告拦截
                         ---> luci-app-smartdns  #SmartDNS本地服务器
                         ---> luci-app-softethervirtual**  #SoftEther virtual**服务器  NAT穿透
                         ---> luci-app-splash  #Client-Splash是无线MESH网络的一个热点认证系统
                         ---> luci-app-sqm  #流量智能队列管理（QOS）
                         ---> luci-app-squid   #Squid代理服务器
                         ---> luci-app-违禁软件-plus   #违禁软件打倒美帝Plus+
                         ---> luci-app-违禁软件-plus ---> Include 违禁软件 New Version  #新SS代理
                         ---> luci-app-违禁软件-plus ---> Include Xray  #Xray代理   *
                         ---> luci-app-违禁软件-plus ---> Include 违禁软件R Server  #违禁软件服务器
                         ---> luci-app-statistics  #流量监控工具
                         ---> luci-app-syncdial  #多拨虚拟网卡（原macvlan）
                         ---> luci-app-syncthing     #Syncthing是一个连续的文件同步程序。它在两台或多台计算机之间同步文件
                         ---> luci-app-tencentddns     #腾讯DDNS
                         ---> luci-app-transmission   #BT下载工具
                         ---> luci-app-ttyd   #网页终端命令行
                         ---> luci-app-unblockmusic  #解锁网易云灰色歌曲3合1新版本
                                 UnblockNeteaseMusic Golang Version  #Golang版本
                                 UnblockNeteaseMusic NodeJS Version  #NodeJS版本
                         ---> luci-app-upnp   #通用即插即用UPnP（端口自动转发）
                         ---> luci-app-uugamebooster  #UU网游加速器   *
                         ---> luci-app-verysync  #微力同步
                         ---> luci-app-vlmcsd  #KMS服务器设置
                                  Include shadowsocks v2ray plugin
                                  Include v2ray
                                  Include trojan
                                  Include ssr s
                         ---> luci-app-watchcat  #断网检测功能与定时重启
                         ---> luci-app-webadmin  #Web管理页面设置
                         ---> luci-app-wifischedule  #WiFi 计划
                         ---> luci-app-wirele违禁软件egdb  #WiFi无线
                         ---> luci-app-wol   #WOL网络唤醒
                         ---> luci-app-wrtbwmon -zn  #实时流量监测
                         ---> luci-app-xlnetacc  #迅雷快鸟
                         ---> luci-app-zerotier  #ZeroTier内网穿透
LuCI  --->  themes  --->  luci-theme-argon     #新的argon主题
                    --->  luci-theme-edge     #主题-edge
                    --->  luci-theme-opentomcat     #主题-opentomcat
                    --->  luci-theme-opentopd     #主题-opentopd
                    --->  luci-theme-atmaterial     #atmaterial-主题
                    --->  luci-theme-rosy     #主题-rosy
                    --->  luci-theme-infinityfreedom     #透明主题
Utilities  --->  Compression  --->  gzip
                              --->  unzip
                              --->  zip
           --->  Disc  --->  blkid（列出分区类型卷标）
                       --->  fdisk（分区工具）
                       --->  lsblk（列出块设备）
                       --->  hdparm（硬盘管理工具）
           --->  Editor  --->  nano（跟vi差不多，但好用）

luci-app-serverchan     #微信推送
