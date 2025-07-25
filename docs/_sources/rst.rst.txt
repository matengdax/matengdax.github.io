reStructuredText
================

标题（Section Titles）
--------------------

=====  ==========
层级    推荐标题符号
=====  ==========
1      =
2      \-
3      ~
4      ^
5      "
6      #
7      \*
8      \+
9      '
=====  ==========

- 每个标题层级用什么标题符号(=,-,~,^,")rst并没有硬性规定
- Simple Table（简单表格）要求每一列的内容宽度要一致，并且分隔线长度要等于最大列的内容宽度


指令块
--------

rst 的“指令块”（directive block）是一种以 ``.. 指令名::`` 开头的特殊语法块，常见的有用于插入特殊内容或结构。

代码块
~~~~

.. code-block:: rst

    .. code:: python
        pass
        
- ``.. code:: [language]``
  
  - reStructuredText（docutils）原生支持的指令
  - 它可以用来插入格式化的代码块，但不自带语法高亮（除非外部工具支持）
  - 可选参数也可以指定语言（如 ``.. code:: python``），但高亮需要额外工具


.. code-block:: rst

    .. code-block:: python
        pass

- ``.. code-block:: [language]``
  
  - Sphinx 对 reStructuredText (rst) 的扩展指令（directive）
  - 支持指定语言并自动高亮
  - 也是 Read the Docs、GitHub rst 渲染、PyPI 等平台支持的主要方式




.. code-block:: rst

    .. directive-name::
       :option1: value1
       :option2: value2

toctree
~~~~

.. code-block:: rst
    
    .. toctree::
    :maxdepth: 2 
    .. 目录树最多显示到第二级标题
    :caption:
    .. 目录标题（可选）

- 这表示“目录树”，自动生成导航
  
  - ``file1``、``file2``、``folder/file3`` 是你要包含到目录树的 rst 文件（不带 .rst 后缀），路径为相对路径
  - 目录树会自动读取这些文件的标题和结构，并按``maxdepth:`` 指定的层级显示
  - folder 目录下要放一个index.rst文件,这个文件里面也要有 torctree 指令块
  - 这个指令块的maxdepth参数一般写1

.. code-block:: rst

    .. image:: logo.png
       :width: 200px
       :align: center
       .. 这是插入图片的指令块

.. code-block:: restructuredtext

    .. 这是一个注释，不会显示在文档里


.. list-table:: 课程表
   :widths: 20 30 50
   :header-rows: 2

   * - 课程
     - 教师
     - 时间
   * - Python 编程
     - 张老师
     - 周一 10:00-12:00
   * - 数据科学
     - 李老师
     - 周三 14:00-16:00


文字块
----

``::`` 文字块（literal block）触发符

- ``::`` 是一种语法标记，用来把后面缩进的内容视为“原文块”或“文字块”，即 literal block
- ``::`` 不是指令块
- ``::`` 让后面的内容按照原样排版，不进行格式解析，常用于代码、命令、输出等


.. code-block:: rst
    
    ::
        .. code-block:: shell
            echo "Hello, World!"


内联代码
-------

.. code-block:: rst

  ``/path/to/source``

.. code-block:: rst

  echo 111111
  # ``/path/to/source``
  # 不会显示内联代码块

rst 代码块内不支持再嵌套“内联代码”

超链接
-----

.. code-block:: rst

  `Google <https://www.google.com/>`_

显示为 ``Google``,且 ``_`` 必不可少