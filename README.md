### V2Ray 基于 Nginx 的 vmess+ws+tls 一键安装脚本

#### 准备

* 准备一个域名，并将A记录添加好。
* [V2ray官方说明](https://www.v2ray.com/) ,了解 TLS WebSocket 及 V2ray 相关信息.
* 安装好 wget.

#### 安装/更新方式（h2 和 ws 版本已合并）

```bash
bash <(curl -s -L https://git.io/Jvn1S)
```
#### 证书

* 如果你已经拥有了你所使用域名的证书文件，可以将 crt 和 key 文件命名为 v2ray.crt v2ray.key 放在 /data 目录下
*（若目录不存在请先建目录），请注意证书文件权限及证书有效期，自定义证书有效期过期后请自行续签
*脚本支持自动生成 let's encrypted 证书，有效期3个月，理论上自动生成的证书支持自动续签

#### 查看客户端配置

`cat ~/v2ray_info.txt`

#### 建议单服务器仅搭建单个代理

* 本脚本默认安装最新版本的V2ray core
* V2ray core 目前最新版本为 4.22.1
* 建议使用默认的443端口作为连接端口
* 伪装内容可自行替换。

#### 注意事项

* 推荐在纯净环境下使用本脚本，如果你是新手，请不要使用Centos系统。
* 程序依赖 Nginx ，请使用 [LNMP](https://lnmp.org) 安装过 Nginx 的用户特别留意，使用本脚本可能会导致无法预知的错误
* V2Ray 的部分功能依赖于系统时间，请确保您使用V2RAY程序的系统 UTC 时间误差在三分钟之内，时区无关。
* 本 bash 依赖于 [V2ray 官方安装脚本](https://install.direct/go.sh) 及 [acme.sh](https://github.com/Neilpang/acme.sh) 工作
* Centos 系统用户请预先在防火墙中放行程序相关端口（默认：80，443）


#### 启动方式

启动 V2ray：`systemctl start v2ray`

停止 V2ray：`systemctl stop v2ray`

启动 Nginx：`systemctl start nginx`

停止 Nginx：`systemctl stop nginx`

#### 相关目录

Web 目录：`/home/wwwroot/3DCEList`

V2ray 服务端配置：`/etc/v2ray/config.json`

V2ray 客户端配置: `~/v2ray_info.txt`

Nginx 目录： `/etc/nginx`

证书文件: `/data/v2ray.key 和 /data/v2ray.crt` 请注意证书权限设置


