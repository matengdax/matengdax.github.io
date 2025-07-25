osx
====

ln
----

.. code-block:: zsh

    ln -sfn /path/to/source /path/to/link

::

    /path/to/source：源文件或目录
    /path/to/link：要创建的链接名

    -s symbolic 创建软链接（符号链接），而不是硬链接。
    -f force 如果目标文件已存在，则强制删除后再创建新链接（覆盖）。
    -n no dereference，如果目标已是符号链接，仅删除链接本身，不跟随其指向的内容

brew
----

.. code-block:: zsh
    
    brew install --cask google-chrome
    # --cask 代表安装图形界面应用（比如谷歌浏览器）

    # brew cask install google-chrome 
    # 旧用法（已废弃）

icloud
------

.. code-block:: bash

    cd ~/Library/Mobile\ Documents/com~apple~CloudDocs/
    # icloud云盘物理路径

diskutil
--------

.. code-block:: bash

    diskutil list
    # 查看磁盘列表

::

    /dev/disk0 (internal, physical):
       #:                       TYPE NAME                    SIZE       IDENTIFIER
       0:      GUID_partition_scheme                        *251.0 GB   disk0
       1:             Apple_APFS_ISC Container disk1         524.3 MB   disk0s1
       2:                 Apple_APFS Container disk3         245.1 GB   disk0s2
       3:        Apple_APFS_Recovery Container disk2         5.4 GB     disk0s3

    /dev/disk3 (synthesized):
       #:                       TYPE NAME                    SIZE       IDENTIFIER
       0:      APFS Container Scheme -                      +245.1 GB   disk3
                                     Physical Store disk0s2
       1:                APFS Volume Macintosh HD            11.3 GB    disk3s1
       2:              APFS Snapshot com.apple.os.update-... 11.3 GB    disk3s1s1
       3:                APFS Volume Preboot                 7.2 GB     disk3s2
       4:                APFS Volume Recovery                1.1 GB     disk3s3
       5:                APFS Volume Data                    208.9 GB   disk3s5
       6:                APFS Volume VM                      2.1 GB     disk3s6

    /dev/disk4 (external, physical):
       #:                       TYPE NAME                    SIZE       IDENTIFIER
       0:      GUID_partition_scheme                        *123.0 GB   disk4
       1:                        EFI EFI                     209.7 MB   disk4s1
       2:       Microsoft Basic Data 128GB                   122.8 GB   disk4s2

.. code-block:: bash

    diskutil unmountDisk /dev/disk4
    # Unmount of all volumes on disk4 was successful
    # 卸载U盘

.. code-block:: bash

    diskutil eraseDisk exFAT <UDISK_NAME> /dev/disk4
    # UDISK_NAME 设置U盘的名称

::

    Started erase on disk4
    Unmounting disk
    Creating the partition map
    Waiting for partitions to activate
    Formatting disk4s2 as ExFAT with name DATA
    Volume name      : DATA
    Partition offset : 411648 sectors (210763776 bytes)
    Volume size      : 239915008 sectors (122836484096 bytes)
    Bytes per sector : 512
    Bytes per cluster: 131072
    FAT offset       : 2048 sectors (1048576 bytes)
    # FAT sectors    : 8192
    Number of FATs   : 1
    Cluster offset   : 10240 sectors (5242880 bytes)
    # Clusters       : 937128
    Volume Serial #  : 6854146c
    Bitmap start     : 2
    Bitmap file size : 117141
    Upcase start     : 3
    Upcase file size : 5836
    Root start       : 4
    Mounting disk
    Finished erase on disk4
    



