# MinerProxy - 作者抽水只有千分之三。
最稳定的ETH以太坊代理中转矿池程序，MinerProxy/矿池代理，支持TCP和SSL协议，支持自定义抽水，高性能高并发，支持web界面管理，包含自启动和进程守护，重启后可以自动运行，会放开防火墙和连接数限制，一键搞定。

# MinerProxy - 使用后算力截图，算力几乎无损耗。

<div align="center">
<img src="https://user-images.githubusercontent.com/96627099/148779614-6ce9006a-6bf3-4c15-87d5-1b3e12ed10b9.png" width="883" height="400" />
</div>

# 矿工交流 QQ群： 308929177

# Liunx-一键安装脚本
好处：适合又想要Linux稳定性的，又不懂Linux的小白的学习者<br />
功能：包含自启动和进程守护，重启后可以自动运行，会放开防火墙和连接数限制，一键搞定<br />
要求：Ubuntu 16+ / Debian 8+ / CentOS 7+ 系统<br />
使用 root 用户输入下面命令安装或卸载<br />
请尽量不要使用国内的腾讯云，阿里云等云服务器。选择国外的CNN回国路线的服务器，请先查阅服务商公司所在地是否不属于国内。

### 输入命令
```bash
wget https://raw.githubusercontent.com/MINErpRroxY/MinerProxy/main/install.sh
bash install.sh
```
### 香港本地公司服务商推荐，低延迟，安全，无需备案。
注册抢购价366一年:链接:https://my.htstack.com/aff.php?aff=7162
先点击右上角快速注册，然后再点击左上角的最新活动，选择第二个云服务器
选择香港服务器366一年超划算。如果你的矿机算力足够大，可以选择第二个款配置。
```

### 查看运行情况（如有被攻击，可以输入查找到对方攻击者IP地址）
```bash
screen -r minerProxy
```

### 退出查看运行情况 键盘键入（然后在安全组中禁止该IP。）
```
ctrl + a + d
```

### 如输入命令后，无法安装，请根据系统版本输入以下命令安装wget
ubuntu/debian 系统安装
```bash
wget: apt-get update -y && apt-get install wget -y
```

centos 系统安装
```bash
yum update -y && yum install wget -y
```

### 提示 curl: command not found的先安装curl
ubuntu/debian 系统安装 curl 方法: 
```bash
apt-get update -y && apt-get install curl -y
```
centos 系统安装 curl 方法: 
```bash
yum update -y && yum install curl -y
```
安装好 curl 之后就能安装脚本了

# Liunx-手动安装（过程要等待）
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
mkdir minerProxy
cd minerProxy
wget https://raw.githubusercontent.com/MINErpRroxY/MinerProxy/main/minerProxy_v5-1_linux -O /root/minerProxy/minerProxy_v5-1_linux
chmod a+x minerProxy_v5-1_linux
nohup ./minerProxy_v5-1_linux & (后台运行，注意：& 也需要复制，运行完再敲几下回车)
cat /root/minerProxy/config.yml
tail -f nohup.out  (后台运行时查看，需要时才输入，输入上面的cat命令获取token已足够)

wget安装命令             yum安装命令               nohup安装命令
apt install wget        apt install  yum          apt install nohup

请尽量不要使用国内的腾讯云，阿里云等云服务器。选择国外的CNN回国路线的服务器，请先查阅服务商公司所在地是否不属于国内。

```

运行成功后访问 IP:18888 (如：127.0.0.1:18888 注意开放端口) 也可以使用关闭防火墙命令进行配置即可。
### 后台运行（注意后面的&）运行完再敲几下回车（不成功的时候看）
```bash
nohup ./minerProxy_v5-1_linux &
```
### 后台运行时关闭
```bash
killall minerProxy_v5-1_linux
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
./minerProxy_v5-1_windows.exe
```
或双击打开minerProxy_v5-1_windows.exe 运行成功后。打开防火墙的18888端口，在网页（谷歌浏览器，edeg浏览器）上输入你的IP:18888，输入token，即可配置

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

# 重点需要观看的参数说明
```bigquery
抽水比例   这里是百分比，填入数字1就是1%
抽水矿池  （抽水去的矿池，比方说可以把鱼池的抽去E池，）
自定义矿机名  （抽水工名字）
钱包地址  顾名思义，抽水的钱包地址
代理矿池  （你转发的矿池挖矿地址，官方的）
本地端口  矿工连接你服务器的端口，比方说222.222.222.222:5678，这里就写5678
注意网页配置
矿池代理比如代理不加密的tcp的请输入 tcp://eth.f2pool.com:6688 如果你要代理加密的SSL ssl://asia2.ethermine.org:5555 记得在安全组打开你端口.否则矿机连不上。
抽水矿池，你要抽到哪里填哪里.ssl加密.需要就开启.不需要就关闭。
```

# 重点需要观看的参数说明：挖矿软件的设置
```bigquery
GMiner连接
TCP端口方式： miner --algo ethash --server {host}:3333 --user {wallet}.{worker} 
SSL加密连接方式： miner --algo ethash --server {host}:14333 --user {wallet}.{worker} --ssl
NBMiner连接
TCP端口方式： nbminer -a ethash -o stratum+tcp://{host}:3333 -u wallet.worker -log 
SSL加密连接方式： nbminer -a ethash -o stratum+ssl://{host}:14333 -u wallet.worker -log
T-REX连接
TCP端口方式： t-rex.exe -a ethash -o stratum+tcp://{host}:3333 -u {wallet} -p x -w {worker} 
SSL加密连接方式： t-rex.exe -a ethash -o stratum+ssl://{host}:14333 -u {wallet} -p x -w {worker} --no-strict-ssl
各种挖矿软件，OS系统
挖矿软件请在矿池管理添加一个矿池，矿池地址如下： 如TCP方式： {host}:3333       SSL方式: {host}:14333
如需要SSL加密方式：开源矿工建议使用GMiner2.74，在高级参数上添加--ssl
OS系统，如使用E池，请选择上面的SSL urls，在下面重新配置个你的IP：地址。
如还有不懂的，在群里有专门的的解答。
```
