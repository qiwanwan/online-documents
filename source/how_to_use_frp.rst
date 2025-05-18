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
1. 下载 frp
   在服务器上下载 frp 的最新版本，可以在 [frp 的 GitHub 页面](https://github.com/fatedier/frp/releases) 上找到最新版本的下载链接。下载完成后，解压缩文件。
   
   这里以 Linux 系统为例，使用以下命令下载和解压缩 frp：
   
   ```bash
   wget https://github.com/fatedier/frp/releases/download/v0.62.1/frp_0.62.1_linux_amd64.tar.gz
   tar -zxvf frp_0.62.1_linux_amd64.tar.gz
   mv frp_0.62.1_linux_amd64 frp

   
2. 配置 frp
