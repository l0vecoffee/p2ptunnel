# p2ptunnel
想和朋友联机玩游戏，下班了需要连接公司电脑，但是自己没有服务器，没有公网ip怎么办

本应用可以建立tcp、udp隧道，把本地或者远程应用端口映射出来，不要求有公网，如果双方节点无法进行直连，会有其它节点进行中继转发，数据端对端加密，中继节点无法查看数据。

## 工作原理

电脑a打开本应用，把一个端口映射出来，电脑b打开本应用，连接电脑a，电脑a的端口映射到本机的127.0.89.1端口下。

如果两台电脑都是内网，会通过其它节点进行数据中继，数据转发的时候会进行端对端加密。

## 使用案例

先下载对于平台的
打开本机的远程桌面，朋友连接帮忙解决问题
### 打开本地端口
./p2ptunnel -type udp -l 3389 

注意这里会输出你的节点id，然后通过聊天软件发给你的朋友，这里假设id是12D3。

### 连接
./p2ptunnel -id 12D3

连接可能需要几秒到1分钟，连接成功后，会输出 Listening tcp 127.0.89.0:3389 -> 3389

然后朋友在远程桌面连接 127.0.89.0:3389 即可。


## 注意事项

1.本应用虽然使用的端对端加密，但是不保证传输数据的安全性，重要数据请勿使用本应用传递。

2.由于是p2p隧道，所以本程序会连接多个ip，如果介意，请使用frp。

## 上游项目

[go-libp2p](/libp2p/go-libp2p)

[p2p-forwarder](/nickname32/p2p-forwarder)