# VPN-in-docker
VPN-in-docker

### Commands
* 生成配置文件
```
docker-compose run --rm openvpn ovpn_genconfig -u tcp://<your IP addredss>
```
* 生成服务器密钥
```
docker-compose run --rm openvpn ovpn_initpki
```

* 启动VPN server
```
docker-compose up -d && docker-compose logs -f
```

* 生产客户端密钥
```
docker-compose exec openvpn rm -rf /etc/openvpn/ca.key
docker-compose exec openvpn easyrsa build-client-full <CLIENT_NANE> nopass
```

* 导出客户端密钥
```
docker-compose exec openvpn ovpn_getclient <CLIENT_NANE> > <CLIENT_NANE>.ovpn
```

### Refs
* https://help.aliyun.com/document_detail/87549.html
* https://github.com/jpetazzo/dockvpn

