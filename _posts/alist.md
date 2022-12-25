# alist

### 一个多功能网盘挂载工具(几乎支持市面上所有的网盘)

[**GitHub项目地址**](https://github.com/alist-org/alist)

[**配置说明文档**](https://alist.nn.ci/zh/guide/)

- docker部署
    - 提前创建挂载目录
    
    ```bash
    mkdir /etc/alist
    ```
    
    - 启动 alist 容器
        
        ```bash
        docker run -d \
        --restart=always \
        -u root \
        -v /etc/alist:/opt/alist/data \
        -p 5244:5244 \
        --name="alist" \
        xhofe/alist:latest
        ```
        
        - 注释
            
            -v 挂载的目录需要提前注释
            
            -u root —> 这项是为了拥有权限访问，不然得配置 alist目录得权限
            
            —restart=always —> 这个表示自动重启
            

- 挂载阿里云网盘
    1. [**获取token**](https://alist.nn.ci/zh/guide/drivers/aliyundrive.html)
    2. 登录到 alist的管理后台，添加存储，如果出现****`failed get storage: can't find storage with rawPath: /`？(这是因为没有添加存储)**
        
        ![Untitled](alist%205afdcecdc4954326a23778b29659c166/Untitled.png)
        
    3. 添加存储
        
        ![Untitled](alist%205afdcecdc4954326a23778b29659c166/Untitled%201.png)
        
        ![Untitled](alist%205afdcecdc4954326a23778b29659c166/Untitled%202.png)
        

### windows 挂载添加的网盘

1. 下载安装[**RaiDrive**](https://www.raidrive.com/)
    - 借助该软件，将 alist 挂载的网盘，弄成是电脑的本地硬盘一样使用
2. 配置RaiDrive 信息
    
    ![Untitled](alist%205afdcecdc4954326a23778b29659c166/Untitled%203.png)
    
    - 注释
        
        IP地址为alist 服务的地址，如果是本机的话，那就是 **127.0.0.1**
        
        端口：默认使用的是 **5244**
        
        路径：注意要写 /dav, 这个是 webdav服务的路径地址
        
3. 最终效果图
    
    ![Untitled](alist%205afdcecdc4954326a23778b29659c166/Untitled%204.png)
    

<aside>
💡 美中不足的是最后挂载显示的容量不准确

</aside>