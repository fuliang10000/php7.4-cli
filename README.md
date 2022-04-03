# laravel环境部署搭建

#### 项目介绍
> 通过docker-compose搭建php环境,包含以下容器服务

- 官方镜像:Nginx
- 官方镜像:mysql
- 官方镜像:redis
- 官方镜像:php
- 工具镜像:基于官方centos搭建,包含软件:git,laravel,php,composer,npm,cnpm,node,vue,taro,yarn,envoy,python,pip等


#### 软件架构
基于docker环境部署
centos+php+mysql+nginx

php框架：laravel

#### 安装前准备
1. 安装docker

#### 安装步骤

1. 下载代码

    ```
    cd ~
    mkdir code
    cd code
    git clone https://gitee.com/zsping1989/laravel.git
    cd laravel
    ```
1. 配置.env文件

1. 启动服务

    ```
    docker-compose up -d
    ```
1. 查看服务启动情况

    ```
    docker-compose ps
    ```

1. 绑定host

    ```
    127.0.0.0.1 www.test.com
    
    ```
1. 完成,通过浏览器访问www.test.com即可

1. 进入工具容器服务继续按照laravel框架代码
    ```
    docker-compose run tool bash
    laravel new ./ --force
    php artisan key:generate
    ```
1. 参照.env.example配置.env文件

1. 完成



#### 使用说明

1. 服务相关配置文件在./docker里面





