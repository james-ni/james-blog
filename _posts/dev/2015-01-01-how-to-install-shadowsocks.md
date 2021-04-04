---
title: "How to install Shadowsocks server side"
date: 2015-01-01T00:00:00+08:00
categories:
  - dev
tags:
  - Shadowsocks
---


In certain scenarios, I need a VPN to access Chinese websites from oversea, or the opposite. Installing Shadowsocks on a cloud server (e.g. AWS or Aliyun) provides a viable solution to meet this use case.

## Prerequisite

- pip


## Steps

1. install Shadowsocks

    ```shell
    pip install shadowsocks
    ```

1. create a config file

    ```shell
    vim /etc/shadowsocks.multiple.json
    ```

    with below content

    ```json
    {
        "server":"0.0.0.0",
        "port_password":{
            "8384":"123456",
            "8385":"456788"
        }
    }
    ```

1. create a startup script
    
    ```shell
    vim /home/sya/ssserver.sh
    ```
    
    with below content
    ```shell
    sudo ssserver -c /etc/shadowsocks.multiple.json -d start
    ```

1. start Shadowsocks server
    
    ```shell
    sh /home/sya/ssserver.sh
    ```


>These steps worked on CentOS. They didn't work on Ubuntu until changing a Python config.