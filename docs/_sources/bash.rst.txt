bash
====

Bash 属于 GNU 项目，是 GNU 操作系统的标准 shell，由自由软件基金会（FSF）维护和发布

Bourne Again SHell

- “Bourne” 来源于最早的 Unix Shell 之一——Bourne Shell（sh），由 Stephen Bourne 编写。
- “Again” 表示 Bash 是对 Bourne Shell 的改进和再实现（“born again” 也有“重生”的双关含义）。
- “Again” 表示 Bash 是对 Bourne Shell 的改进和再实现（“born again” 也有“重生”的双关含义）。

Bash 是 GNU 项目下开发的类 Unix shell，兼容 sh，并增加了许多功能，比如命令补全、命令历史等

内置命令（builtin）
------

内置命令：是 shell 内部实现的命令，用于执行具体操作

.. list-table:: Bash 内置命令（builtins）一览
   :header-rows: 1

   * - 命令
     - 说明
   * - : 
     - 空命令，什么也不做（no-op）
   * - .
     - 执行脚本文件（source）
   * - [
     - 条件测试（与 test 命令相同）
   * - alias
     - 定义或显示别名
   * - bg
     - 将作业放到后台运行
   * - bind
     - 绑定键盘按键
   * - break
     - 跳出循环
   * - builtin
     - 运行指定的内置命令
   * - caller
     - 返回子 shell 的调用信息
   * - cd
     - 切换当前目录
   * - command
     - 忽略别名和函数，执行命令
   * - compgen
     - 产生可能的补全列表
   * - complete
     - 为命令指定补全规则
   * - compopt
     - 修改补全行为
   * - continue
     - 继续下一轮循环
   * - declare
     - 声明变量和赋值属性
   * - dirs
     - 显示目录栈
   * - disown
     - 移除作业，使其不再与 shell 关联
   * - echo
     - 输出字符串
   * - enable
     - 启用或禁用内置命令
   * - eval
     - 重新求值参数形成的字符串
   * - exec
     - 用指定命令替换 shell
   * - exit
     - 退出 shell
   * - export
     - 设置环境变量
   * - false
     - 返回非成功状态（1）
   * - fc
     - 命令历史操作（fix command）
   * - fg
     - 将后台作业调入前台
   * - getopts
     - 解析命令行参数
   * - hash
     - 管理命令的路径查找表
   * - help
     - 显示内置命令的帮助信息
   * - history
     - 显示或操作历史命令
   * - jobs
     - 显示作业状态
   * - kill
     - 发送信号终止进程
   * - let
     - 进行算术运算
   * - local
     - 声明局部变量
   * - logout
     - 退出登录 shell
   * - mapfile
     - 从标准输入读入数组
   * - popd
     - 删除目录栈顶目录
   * - printf
     - 格式化输出
   * - pushd
     - 将目录压入目录栈
   * - pwd
     - 显示当前目录
   * - read
     - 读取一行标准输入
   * - readarray
     - 读取标准输入到数组（同 mapfile）
   * - readonly
     - 声明只读变量
   * - return
     - 从函数返回
   * - set
     - 设置 shell 选项和参数
   * - shift
     - 移动参数
   * - shopt
     - 设置 shell 选项
   * - source
     - 执行脚本文件内容（同 .）
   * - suspend
     - 挂起 shell
   * - test
     - 条件测试
   * - times
     - 显示 shell 和其子进程的累计时间
   * - trap
     - 指定接收到信号时要采取的动作
   * - true
     - 返回成功状态（0）
   * - type
     - 显示命令类型（内置、外部等）
   * - typeset
     - 声明变量属性（declare 的同义词）
   * - ulimit
     - 显示或设置用户进程资源限制
   * - umask
     - 显示或设置文件模式创建掩码
   * - unalias
     - 删除别名
   * - unset
     - 删除变量或函数
   * - wait
     - 等待后台作业完成

.. note::

   在终端输入 ``help`` 查看所有 Bash 支持的内置命令，并可用 ``help 命令名`` 获取某个命令的详细帮助。

eval
~~~~

- ``eval`` 是英文单词 ``evaluate`` 的缩写，意思是“求值”“计算”“执行”。
- 在编程和命令行中，eval 表示“把参数当作代码再执行一次”。
- eval 的作用是：把它后面的参数组合成一个字符串，再让 Shell 把这个字符串当作命令来执行一遍。
- 它经常用于动态生成命令、变量间接引用、多级展开等场景。

.. code-block:: bash

    varname="HOME"
    eval echo \$$varname

::

    第一个$会被转义成字面量$
    “字面量”是编程中的一个术语，指的是在代码中直接写出来的具体值。
    它不是变量，也不是表达式的计算结果，而是明确写在代码里的常量数值、字符等
    第二个 $varname 展开成 HOME，拼起来就是 $HOME

.. code-block:: bash

    cmd="ls -l"
    eval $cmd
    # ls -l

多级变量嵌套
^^^^^^^^^^

.. code-block:: bash

    var1="world"
    var2="var1"
    eval echo \$${var2}
    # eval echo $var1
    # echo $var1，输出 world

compgen
~~~~~~~

-b 显示所有内置命令
^^^^^^^^^^^^^^^^

::

    .
    :
    [
    alias
    bg
    bind
    break
    builtin
    caller
    cd
    command
    compgen
    complete
    compopt
    continue
    declare
    dirs
    disown
    echo
    enable
    eval
    exec
    exit
    export
    false
    fc
    fg
    getopts
    hash
    help
    history
    jobs
    kill
    let
    local
    logout
    mapfile
    popd
    printf
    pushd
    pwd
    read
    readarray
    readonly
    return
    set
    shift
    shopt
    source
    suspend
    test
    times
    trap
    true
    type
    typeset
    ulimit
    umask
    unalias
    unset
    wait

-k 显示所有保留字
^^^^^^^^^^^^^^

::

    if
    then
    else
    elif
    fi
    case
    esac
    for
    select
    while
    until
    do
    done
    in
    function
    time
    {
    }
    !
    [[
    ]]
    coproc

内置保留字(reserved)
--------

内置关键词是 shell 语法的一部分，称为“保留字”（reserved words）。

这些词汇在 shell 解释器中有特殊的语法作用，用于控制流程、定义结构等。

它们不是命令，不能作为普通变量名或函数名使用。

``[]``, ``[[ ]]``, ``(( ))``, ``()`` 并不是保留字（reserved words）

而是 Bash 语法中的特殊操作符或结构符号

.. list-table:: Bash 内置关键词及示例
   :header-rows: 1

   * - 关键词
     - 作用
     - 示例
   * - if
     - 条件语句
     - if [ ... ]; then ... fi
   * - then
     - if 结构的一部分
     - 
   * - else
     - if 结构的一部分
     - 
   * - elif
     - if 结构的一部分
     - 
   * - fi
     - if 结构结束
     - 
   * - for
     - 循环语句
     - for i in 1 2 3; do ... done
   * - in
     - for 结构的一部分
     - 
   * - do
     - for/while 结构的一部分
     - 
   * - done
     - for/while 结构结束
     - 
   * - while
     - 循环语句
     - while [ ... ]; do ... done
   * - until
     - 循环语句
     - 
   * - case
     - 多分支选择结构
     - case $var in ... esac
   * - esac
     - case 结构结束
     - 
   * - function
     - 定义函数
     - function foo { ... }
   * - select
     - 菜单选择结构
     - 
   * - time
     - 计时执行命令
     - 
   * - { }
     - 命令组
     - { echo 1; echo 2; }
   * - !
     - 逻辑非
     - ! command
   * - [[ ]]
     - 测试条件
     - [[ $a -eq $b ]]
   * - (( ))
     - 算术运算
     - (( a++ ))
   * - break
     - 跳出循环
     - 
   * - continue
     - 继续下一轮循环
     - 
   * - return
     - 从函数返回
     - 

[[ ... ]]
~~~~~~~~~

.. note::

    Bash 的保留字可以通过 ``compgen -k`` 查看

(( ... ))
~~~~~~~~~

aaa

example
-------

'...' 和 "..." 等价吗?
~~~~~~~~~~~~~~~~~~~~~

不等价，双引号会展开变量，单引号不会
