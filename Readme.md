## 需要修改的部分
1. `./docker-compose.yaml`填上伪装页面的域名(2处)  

2. `./reality/config.json`找到`"secretKey": ""`，在双引号中填入warp的PrivateKey。找到`"publicKey": ""`，在双引号中填入warp的PublicKey。如果不想启用warp处理访问中国大陆的流量，将所有的`"outboundTag": "wireguard-1"`改成`"outboundTag": "direct"`(2处)。
3. 在启动容器前，先使用acme.sh或其他工具为伪装域名申请证书，并安装至`./data/certs`，分别为`fullchain.pem`(使用证书链文件可以提高安全性)和`key.pem`。推荐使用`acme.sh --install-cert -d xxxx --fullchain-file xxx --key-file xxx`安装证书，使用dns api申请证书，以实现自动证书配置。