SSH连接如何不输入密码
=====================

SSH连接不输入密码可以通过使用SSH密钥对来实现。

本地操作
--------
首先需要在本地机器上生成SSH密钥对，并将公钥添加到远程服务器的`~/.ssh/authorized_keys`文件中。

.. code-block:: sh
   :caption: 生成SSH密钥对
   :name: test333
   :emphasize-lines: 2
   :linenos:

   #生成SSH密钥对，按3次回车即可
   ssh-keygen -t rsa
   #获取公钥内容
   cat ~/.ssh/id_rsa.pub



远程操作
--------
将本地公钥添加到远程服务器的`~/.ssh/authorized_keys`文件中。

