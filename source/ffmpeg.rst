ffmpeg
====


.. code-block:: bash

    ffmpeg -i input_file -ac 1 -ar 16000 outputfile
    # -ac 1 转换为1声道（单声道）
    # -ar 16000 采样率设置为16kHz
.. code-block:: bash

    ffmpeg -ss 10 -i input.mp4 -t 20 output.mp4
    # 从第10秒开始，截取20秒