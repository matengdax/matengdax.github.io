sox
====

`SoX - Sound eXchange <https://sourceforge.net/projects/sox/files/>`_

是一个开源、跨平台的音频处理工具，被誉为音频处理领域的“瑞士军刀”。它可以在命令行下完成多种音频文件的转换、编辑和处理任务，广泛应用于音频批量处理、格式转换、特效添加、采样率变换、音频剪切合并等场景。

SoX项目虽然正式release停留在2014年，但它的代码仓库（如GitHub、SourceForge SVN等）偶尔还有维护或bugfix提交，部分Linux/BSD社区会基于最新源码打包“非官方预览版”或“补丁版”。

有了ffmpeg为什么还需要sox
----

- **ffmpeg** 和 **sox** 都是功能强大的音频处理工具，但各有侧重。
- **ffmpeg** 是全能型多媒体处理工具，支持音视频编解码、转码、处理、流媒体等；音频功能丰富，但对音频“特效处理”不是很专业
- **sox** 专注于音频领域，尤其擅长 **批量音频处理、特效、滤波、格式转换等**，被称为“音频界的瑞士军刀”。








sox比ffmpeg强在哪
~~~~

- **音频特效和滤波器丰富**：支持几十种特效，如 reverb、compand、chorus、phaser、pitch shift、equalizer、noise reduction 等。
- **批量处理与脚本化友好**：sox 内置命令行参数非常适合批处理，音频处理链条直观。
- **命令简洁**：很多音频专用操作，sox 的命令要比 ffmpeg 简单明了。
- **体积小**：sox 安装包小，依赖少。

.. code-block:: bash

    sox input.wav output.wav trim 0 10   # 截取前10秒
