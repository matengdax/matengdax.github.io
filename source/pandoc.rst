pandoc
======

.. code-block:: bash

    pandoc example.md -f markdown -t rst -o example.rst
    # md转rst
    # -f markdown 指定输入格式是 Markdown（可以省略，pandoc能自动识别）
    # -t rst 指定输出格式是 reStructuredText
    # -o example.rst 指定输出文件名