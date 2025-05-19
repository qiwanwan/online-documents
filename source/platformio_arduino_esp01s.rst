PlatformIO 对 ESP-01S 编程注意事项
===============================

使用 PlatformIO 通过 Arduino 框架对 ESP-01S 进行编程时，程序无法运行！！怎么办？？？配置文件最后 **添加一下两条高亮语句**

.. code-block:: ini
   :caption: platformio.ini
   :emphasize-lines: 5,6

    [env:esp01_1m]
    platform = espressif8266
    board = esp01_1m
    framework = arduino
    board_upload.resetmethod = nodemcu
    board_build.flash_mode = dout
