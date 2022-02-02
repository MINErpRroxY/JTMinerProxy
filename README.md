# MinerProxy - 以修改作者抽水至千分之三。
最稳定的ETH以太坊代理中转矿池程序，MinerProxy/矿池代理，支持TCP和SSL协议，支持自定义抽水，高性能高并发，支持web界面管理，包含自启动和进程守护，重启后可以自动运行，会放开防火墙和连接数限制，一键搞定。

# MinerProxy - 使用后算力截图，算力几乎无损耗。

<div align="center">
<img src="https://user-images.githubusercontent.com/96627099/148779614-6ce9006a-6bf3-4c15-87d5-1b3e12ed10b9.png" width="883" height="400" />
</div>

# 矿工交流 QQ群： 308929177


# Liunx-手动安装
```bash
常用命令
root权限开启
输入su root 
再输入密码

防火墙相关命令
1.防火墙打开
sudo ufw enable
2.防火墙重启
sudo ufw reload
3.打开想要的端口（以9000为例）
ufw allow 9000
4.查看本机端口使用情况
ufw status
5.关闭防火墙
sudo ufw disable

进入服务器root权限后可复制以下代码，一一输入。输入完一个回车一次，接着输入第二个命令。
git clone https://github.com/MINErpRroxY/MinerProxy.git
cd MinerProxy
chmod a+x minerProxy_3.0.3_linux
nohup ./minerProxy_3.0.3_linux & (后台运行，注意：& 也需要复制，运行完再敲几下回车)
tail -f nohup.out (后台运行时查看)
```

运行成功后访问 IP:18888 (如：127.0.0.1:18888 注意开放端口) 也可以使用关闭防火墙命令进行配置即可。
### 后台运行（注意后面的&）运行完再敲几下回车
```bash
nohup ./minerProxy_3.0.3_linux &
```
### 后台运行时关闭
```bash
killall minerProxy_3.0.3_linux
```
### 后台运行时查看
```bash
tail -f nohup.out
```
## 提示bash: git: command not found的先安装git
### ubuntu下
```bash
apt update
apt install git
```
### centos下
```bash
yum update
yum install git
```
# Windows-使用方法
```bash
./minerProxy_3.0.3_windows.exe
```
或双击打开minerProxy_3.0.3_windows.exe 运行成功后。打开防火墙的18888端口，在网页（谷歌浏览器，edeg浏览器）上输入你的IP:18888，输入token，即可配置

# 配置文件 config.yml
```
host: 0.0.0.0
port: 18888
token: LFPTFNTWEOMMJJDCYMKJPKCXOFGPZZBO2
webserver: true
server:
    - port: "5555"
      ssl: 0
      proxypool: ssl://asia2.ethermine.org:5555
      devfee: 0.5
      devpool: ssl://asia2.ethermine.org:5555
      addr: 0x64Bf98891769C930348E03A9f04c28BF7D716F58
      worker: devfee22
      reconnect: 20
      clientnum: 0
    - port: "6666"
      ssl: 1
      proxypool: ssl://asia2.ethermine.org:5555
      devfee: 0.5
      devpool: ssl://asia2.ethermine.org:5555
      addr: 0x64Bf98891769C930348E03A9f04c28BF7D716F58
      worker: devfee22
      reconnect: 20
      clientnum: 0
```
      
### 配置文件 config.yml 说明
```
host: 0.0.0.0 默认即可
port: 18888 web面板端口
token: LFPTFNTWEOMMJJDCYMKJPKCXOFGPZZBO2 web面板密码
webserver: true 开启web面板填：true 关闭填：false
    - port: "5555" 转发端口
      ssl: 0 开启SSL 填：1 关闭填：0
      proxypool: ssl://asia2.ethermine.org:5555 转发矿池地址
      devfee: 0.5 抽水比例
      devpool: ssl://asia2.ethermine.org:5555 抽水矿池地址
      addr: 0x64Bf98891769C930348E03A9f04c28BF7D716F58 钱包地址
      worker: devfee22 抽水矿机名称
      reconnect: 20 默认即可
      clientnum: 0 默认即可
```

# 参数说明
```bigquery
抽水比例   这里是百分比，填入数字1就是1%
抽水矿池  （抽水去的矿池，比方说可以把鱼池的抽去E池，）
自定义矿机名  （抽水工名字）
钱包地址  顾名思义，抽水的钱包地址
代理矿池  （你转发的矿池挖矿地址，官方的）
本地端口  矿工连接你服务器的端口，比方说222.222.222.222:5678，这里就写5678
```
