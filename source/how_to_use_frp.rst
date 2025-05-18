内网穿透frp
==========================


内网穿透是指在内网环境中，将内网服务暴露到公网上的技术。它可以让外部用户访问内网中的服务，而不需要进行复杂的网络配置。内网穿透通常用于远程访问、远程控制、远程调试等场景。
frp 是一个高性能的反向代理应用，专注于内网穿透。它可以将内网服务暴露到公网上，方便外部访问。frp 的使用非常简单，只需要在内网和公网各部署一个 frp 实例即可。

frp 的工作原理
----------------------------
frp 的工作原理是通过在内网和公网之间建立一个长连接，将内网服务的请求转发到公网。具体来说，frp 在内网和公网各部署一个 frp 实例，内网实例负责将内网服务的请求转发到公网实例，公网实例负责将外部请求转发到内网实例。这样就实现了内网穿透。
frp 的工作原理如下图所示：

.. image:: _static/frp_workflow.png
    :width: 600px
    :height: 400px
    :align: center
    :alt: frp 工作原理
    :scale: 100%
    
服务器端部署
----------------------------

服务器必须有 **公网IP** 地址，且可以访问互联网。frp 的服务器端称为 frps，客户端称为 frpc。frps 负责接收来自 frpc 的请求，并将请求转发到内网服务。

1. 下载 frp

   在服务器上下载 frp 的最新版本，可以在 [frp 的 GitHub 页面](https://github.com/fatedier/frp/releases) 上找到最新版本的下载链接。下载完成后，解压缩文件。
   这里以 Linux 系统为例，使用以下命令下载和解压缩 frp：

.. code-block:: sh
   :caption: 下载 frp，Linux 系统
   :name: test333
   :emphasize-lines: 2
   :linenos:

   #下载
   wget https://github.com/fatedier/frp/releases/download/v0.62.1/frp_0.62.1_linux_amd64.tar.gz
   #解压
   tar -zxvf frp_0.62.1_linux_amd64.tar.gz
   #重命名解压后的文件夹为 frp
   mv frp_0.62.1_linux_amd64 frp

   
2. 配置 frp

    进入 frp 目录，找到 frps.toml 文件。该文件是 frp 的配置文件，包含了 frp 的基本配置和服务端口的设置。可以使用文本编辑器打开该文件进行编辑。
    下面是一个简单的 frps.toml 配置文件示例：

.. code-block:: toml
   :caption: frps.toml 配置文件
   :name: test444
   :linenos:

   #客户端连接端口，默认7000
   bind_port = 7000
   #web界面网址，默认为 127.0.0.1，如果需要公网访问，需要修改为 0.0.0.0。
   webServer.addr = "0.0.0.0"
   #web界面端口，默认7500
   webServer.port = 7500
   #web界面用户名密码，可选，默认为空
   webServer.user = "admin"
   webServer.password = "admin"
   
3. 启动 frp

    在 frp 目录下，使用以下命令启动 frps：
    
.. code-block:: sh
   :caption: 启动 frps
   :name: test555
   :linenos:

   #启动 frps
   ./frps -c ./frps.toml