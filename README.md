# rancher nginx ssl

```bash

sudo docker run --restart=always -p 80:80 -p 443:443 --link <rancher_name>:rancher-server --name rancher-nginx-ssl -d -e EMAIL=<your_email> -e DOMAIN=<your_domain> bteton/rancher-nginx-ssl
```

```bash
# Specify a volume to store your certificates on the host. They will be stored when you remove the container etc.

sudo docker run --restart=always -p 80:80 -p 443:443 -v <host_vol>:/etc/letsencrypt --link <rancher_name>:rancher-server --name rancher-ssl -d -e EMAIL=<your_email> -e DOMAIN=<your_domain> bteton/rancher-nginx-ssl
```

进入容器检查:

```bash
docker logs --follow rancher-nginx-ssl
```
start.sh 作用：

nginx在ngx_init_cycle中会调用ngx_conf_param 和ngx_conf_parse进行配置文件的解析，其中ngx_conf_param是基于ngx_conf_parse实现的

ngx_conf_param负责解析nginx命令行参数’-g’加入的配置。ngx_conf_parse负责解析nginx配置文件

https://hub.docker.com/r/balldog/rancher-nginx-ssl/

## 注意

rancher1.6版本请用 balldog/rancher-nginx-ssl:1.6
最新的用latest既可以。
