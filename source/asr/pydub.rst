pydub
=====

`pydub <https://github.com/jiaaro/pydub>`_

pydub 本质上是一个用 Python 编写的、针对音频处理的高层封装库

它的核心作用是：

让你用非常简单的 Python 语法，完成“音频的切割、拼接、淡入淡出、格式转换、音量调整”等常见操作，而不用直接操作底层的音频数据格式。

pydub本质是音频处理的“胶水层”：pydub 并不直接实现音频的底层编解码、格式解析等，而是封装并调用了 ffmpeg 或 avlib 这些成熟的第三方音频工具

pydub 本质是一个音频处理的 Python 封装库，底层依赖 ffmpeg，简化了音频相关的操作