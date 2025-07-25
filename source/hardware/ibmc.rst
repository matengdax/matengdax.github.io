IPMC 命令参考
==============

help
----

::

    Commands:
    help      :       Used to get context sensitive help.
    exit      :       Used to terminate the CLP session.
    ipmcget   :       Used to get BMC runtime status.
    ipmcset   :       Used to set BMC runtime status or send control command.
    notimeout :       Used to set no timeout limit to login shell.
    maint_debug_cli : Used to maintance in debug mode.
    ping      :       Used to test IPv4 network status.
    ping6     :       Used to test IPv6 network status.
    ifconfig  :       Used to check network device information.
    free      :       Used to check memory status.
    top       :       Used to check system resource used information. None parameter is allowed
    df        :       Used to check disk used information.
    route     :       Used to check route information. None parameter is allowed
    netstat   :       Used to check network port status.

ipmcget
-------

::

    Usage: ipmcget [-t target] -d dataitem [-v value]
        -t <target>
           fru0                          Get the information of the fru0
           sensor                        Print detailed sensor information
           smbios                        Get the information of smbios
           trap                          Get SNMP trap status
           service                       Get service information
           maintenance                   Get maintenance information
           syslog                        Get syslog status
           user                          Get the information of user
           securitybanner                Get login security banner information
           vnc                           Get VNC information
           storage                       Get storage device information
           config                        Get configuration information
           vmm                           Get Virtual Media information
           certificate                   Get SSL certificate information
           sol                           Get SOL information
           securityenhance               Get security enhance information

        -d <dataitem>
           faninfo                       Get fan mode and the percentage of the fan speed
           port80                        Get the diagnose code of port 80
           diaginfo                      Get diagnostic info of management subsystem
           systemcom                     Get system com data
           blackbox                      Get black box data
           bootdevice                    Get boot device
           shutdowntimeout               Get graceful shutdown timeout state and value
           powerstate                    Get power state
           health                        Get health status
           healthevents                  Get health events
           sel                           Print System Event Log (SEL)
           operatelog                    Print operation log
           version                       Get iBMC version
           serialnumber                  Get system serial number
           userlist                      List all user info
           fruinfo                       Get fru information
           time                          Get system time
           macaddr                       Get mac address
           serialdir                     Get currently connected serial direction
           rollbackstatus                Get rollback status
           passwordcomplexity            Get password complexity check enable status
           ledinfo                       Get led information
           ipinfo                        Get ip information
           ethport                       Get usable eth port
           psuinfo                       Get PSU component information
           autodiscovery                 Get autodiscovery configuration
           poweronpermit                 Get poweronpermit configuration
           minimumpasswordage            Get minimum password age configuration
           ntpinfo                       Get NTP information
           notimeoutstate                Get CLI session notimeout state

-t <target>
~~~~~~~~~~~

::

    fru0                          Get the information of the fru0
    sensor                        Print detailed sensor information
    smbios                        Get the information of smbios
    trap                          Get SNMP trap status
    service                       Get service information
    maintenance                   Get maintenance information
    syslog                        Get syslog status
    user                          Get the information of user
    securitybanner                Get login security banner information
    vnc                           Get VNC information
    storage                       Get storage device information
    config                        Get configuration information
    vmm                           Get Virtual Media information
    certificate                   Get SSL certificate information
    sol                           Get SOL information
    securityenhance               Get security enhance information


-d <dataitem>
~~~~~~~~~~~~~

::

    ctrlinfo                      Get the information of RAID controller
    ldinfo                        Get the information of logical drive
    pdinfo                        Get the information of physical drive
    arrayinfo                     Get the information of disk array

pdinfo
^^^^^^

::

    Usage: ipmcget -t storage -d pdinfo 
    Option:
        all - Show all physical drives.
        ID  - Show only one physical drive which matches with this ID (0 - 255).

-v <Option>
"""""""""""""""

**0|1**

all
""""

.. code-block:: bash

    ipmcget -t storage -d pdinfo -v al

::

    Physical Drive Information
    ----------------------------------------------------------------------
    ID                                       : 0
    Device Name                              : Disk0
    Manufacturer                             : HUAWEI
    Serial Number                            : 034BBTFSMA023591
    Model                                    : HWE62ST3480L003N
    Firmware Version                         : 1086
    Health Status                            : Normal
    Firmware State                           : ONLINE
    Power State                              : Spun Up
    Media Type                               : SSD
    Interface Type                           : SATA
    Capable Speed                            : 6.0 Gbps
    Negotiated Speed                         : 6.0 Gbps
    Drive Temperature                        : 29(Celsius)
    Capacity                                 : 446.625 GB
    Hot Spare                                : None
    Rebuild in Progress                      : No
    Patrol Read in Progress                  : No
    Remnant Media Wearout                    : 100%
    Power-On Hours                           : 131
    SAS Address(0)                           : 300062b20b29cb44
    SAS Address(1)                           : 0000000000000000
    Location State                           : Off
    Bootable                                 : No
    Boot Priority                            : None

    Media Error Count                        : 0
    Prefail Error Count                      : 0
    Other Error Count                        : 0
    ----------------------------------------------------------------------

    Physical Drive Information
    ----------------------------------------------------------------------
    ID                                       : 1
    Device Name                              : Disk1
    Manufacturer                             : HUAWEI
    Serial Number                            : 034BBTFSM9006954
    Model                                    : HWE62ST3480L003N
    Firmware Version                         : 1086
    Health Status                            : Normal
    Firmware State                           : ONLINE
    Power State                              : Spun Up
    Media Type                               : SSD
    Interface Type                           : SATA
    Capable Speed                            : 6.0 Gbps
    Negotiated Speed                         : 6.0 Gbps
    Drive Temperature                        : 28(Celsius)
    Capacity                                 : 446.625 GB
    Hot Spare                                : None
    Rebuild in Progress                      : No
    Patrol Read in Progress                  : No
    Remnant Media Wearout                    : 100%
    Power-On Hours                           : 132
    SAS Address(0)                           : 300062b20b29cb45
    SAS Address(1)                           : 0000000000000000
    Location State                           : Off
    Bootable                                 : No
    Boot Priority                            : None

    Media Error Count                        : 0
    Prefail Error Count                      : 0
    Other Error Count                        : 0
    ----------------------------------------------------------------------

ctrlinfo
""""""""

::

    Usage: ipmcget -t storage -d ctrlinfo -v <Option>
    Option:
            all   - Show all RAID controllers.
            ID    - Show one RAID controller with this ID(An non-negative integer base 0). eg. 0,1,2...

-v <Option>
""""""""""""

all
""""

.. code-block:: bash

    ipmcget -t storage -d ctrlinfo -v all

::

    RAID Controller #0 Information
    ----------------------------------------------------------------------
    Controller Name                               : MegaRAID 9560-8i 4GB
    Controller Type                               : SAS3908
    Component Name                                : PCIe Card 1 (9560-8i)
    Support Out-of-Band Management                : Yes
    Supported RAID Levels                         : RAID(0/1/5/6/10/50/60)
    Controller Mode                               : RAID
    Controller Health                             : Normal
    Firmware Version                              : 5.200.02-3618
    NVDATA Version                                : 5.2000.00-0511
    Memory Size                                   : 4096 MB
    Device Interface                              : SAS 12G
    SAS Address                                   : 500062b20b29cb40
    Minimum Strip Size Supported                  : 64 KB
    Maximum Strip Size Supported                  : 1 MB
    Controller Cache Is Pinned                    : No
    Maintain PD Fail History across Reboot        : Yes
    Copyback Enabled                              : Yes
    Copyback on SMART error Enabled               : No
    JBOD Enabled                                  : N/A
    DDR ECC Count                                 : 0
    Primary Boot Device                           : Logical Drive 5
    Secondary Boot Device                         : None

    BBU Status                                    : Present
    BBU Type                                      : CVPM05
    BBU Health                                    : Normal

    PHY Status                                    :
            PHY #0 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #1 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #2 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #3 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #4 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #5 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #6 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0

            PHY #7 :
                    Invalid Dword Count           : 0
                    Loss Dword Sync Count         : 0
                    PHY Reset Problem Count       : 0
                    Running Disparity Error Count : 0
    ----------------------------------------------------------------------

user
~~~~

-d <dataitem>
^^^^^^^^^^^^^^

::

    list                          List all user info
    passwordcomplexity            Get password complexity check enable status
    sshpasswordauthentication     Get SSH password authentication status
    usermgmtbyhost                Get user management status on the host side

list
"""""

.. code-block:: bash

    ipmcget -t user -d list

::

    ID      Name              Privilege      Interface                                       PublicKeyHash                                   State
    2       Tech.ON           ADMINISTRATOR  Web,SNMP,IPMI,SSH,SFTP,Local,Redfish            NA                                              Enabled
    3       Administrator     ADMINISTRATOR  Web,SNMP,IPMI,SSH,SFTP,Local,Redfish            NA                                              Enabled
    4                         NO ACCESS                                                      NA                                              Disabled
    5                         NO ACCESS                                                      NA                                              Disabled
    6                         NO ACCESS                                                      NA                                              Disabled
    7                         NO ACCESS                                                      NA                                              Disabled
    8                         NO ACCESS                                                      NA                                              Disabled
    9                         NO ACCESS                                                      NA                                              Disabled
    10                        NO ACCESS                                                      NA                                              Disabled
    11                        NO ACCESS                                                      NA                                              Disabled
    12                        NO ACCESS                                                      NA                                              Disabled
    13                        NO ACCESS                                                      NA                                              Disabled
    14                        NO ACCESS                                                      NA                                              Disabled
    15                        NO ACCESS                                                      NA                                              Disabled
    16                        NO ACCESS                                                      NA                                              Disabled
    17                        NO ACCESS                                                      NA                                              Disabled

ipinfo
~~~~~~~

.. code-block:: bash

    ipmcget -d ipinfo

::

    EthGroup ID               :  1
    Net Mode                  :  Manual
    Net Type                  :  Dedicated
    IPv4 Information          :
    IP Mode                   :  static
    IP Address                :  172.21.27.69
    Subnet Mask               :  255.255.248.0
    Default Gateway           :  172.21.31.254
    Backup IP Address         :  192.168.2.100 (Deactivated)
    Backup Subnet Mask        :  255.255.255.0 (Deactivated)
    MAC Address               :  8c:2a:8e:96:35:b4
    IPv6 Information          :
    IPv6 Mode                 :  static
    IPv6 Address 1            :
    Default Gateway IPv6      :
    Link-Local Address        :  fe80::8e2a:8eff:fe96:35b4/64
    VLAN Information          :
    NCSI Port VLAN State      :  disabled
    Dedicated Port VLAN State :  disabled

macaddr
~~~~~~~

.. code-block:: bash

    ipmicget -d macaddr

- 获取的是四个电口mac地址，不是IPMI电口mac地址

::

    Net Card Name | Port Name  | Mac Address
    NIC 1 (TM210) | Port1      | 8C:2A:8E:96:35:B6
    NIC 1 (TM210) | Port2      | 8C:2A:8E:96:35:B7
    NIC 1 (TM210) | Port3      | 8C:2A:8E:96:35:B8
    NIC 1 (TM210) | Port4      | 8C:2A:8E:96:35:B9
    PCIe Card 2   | Port1      | 00:00:00:00:00:00
    PCIe Card 2   | Port2      | 00:00:00:00:00:00
    PCIe Card 2   | Port3      | 00:00:00:00:00:00
    PCIe Card 2   | Port4      | 00:00:00:00:00:00

ntpinfo
~~~~~~~

.. code-block:: bash

    ipmcget -d ntpinfo

::

    Status             : enabled
    Mode               : manual
    Preferred Server   : 172.21.66.13
    Alternative Server : 172.21.66.13
    Extra Server       :
    Synchronize        : successful
    Auth Enable        : disabled
    Group Key          : not imported

version
~~~~~~~

.. code-block:: bash

    ipmcget -d version

::

    ------------------- iBMC INFO -------------------
    IPMC               CPU:           Hi1711
    IPMI           Version:           2.0
    CPLD           Version:           (U6076)6.15
    Active iBMC    Version:           (U82)3.03.00.67
    Active iBMC      Build:           001
    Active iBMC      Built:           02:24:31 Mar 31 2023
    Backup iBMC    Version:           3.03.00.67
    Available iBMC Version:           3.03.00.67
    Available iBMC   Build:           001
    SDK            Version:           16.2.10.1
    SDK              Built:           15:42:08 Feb 25 2023
    Active Uboot   Version:           16.2.10.1 (15:49:59 Feb 25 2023)
    Backup Uboot   Version:           16.2.10.1 (15:49:59 Feb 25 2023)
    Active Secure Bootloader Version: 16.2.10.1 (15:49:48 Feb 25 2023)
    Backup Secure Bootloader Version: 16.2.10.1 (15:49:48 Feb 25 2023)
    Active Secure Firmware   Version: 16.2.10.1 (15:49:48 Feb 25 2023)
    Backup Secure Firmware   Version: 16.2.10.1 (15:49:48 Feb 25 2023)
    ----------------- Product INFO -----------------
    Product             ID:           0x0007
    Product           Name:           TG225 A1
    Active BIOS    Version:           (U75)6.55
    Backup BIOS    Version:           6.55
    -------------- Mother Board INFO ---------------
    Mainboard      BoardID:           0x00a9
    Mainboard          PCB:           .A
    ------------------- NIC INFO -------------------
    NIC 1 (TM210)  BoardID:           0x0068
    NIC 1 (TM210)      PCB:           .A
    --------------- Riser Card INFO ----------------
    Riser1       BoardName:           BC82PRUA
    Riser1         BoardID:           0x0094
    Riser1             PCB:           .A
    -------------- HDD Backplane INFO --------------
    Disk BP1      BoardName:          BC11HBBB
    Disk BP1       BoardID:           0x007c
    Disk BP1           PCB:           .A
    Disk BP1     CPLD Version:        (U2)2.01
    -------------------- PSU INFO -------------------
    PSU1            Version:           DC:108 PFC:108
    PSU2            Version:           DC:108 PFC:108

serialnumber
~~~~~~~~~~~~

.. code-block:: bash

    ipmcget -d serialnumber

::

    System SN is:2102314CRA10P3100012

serialdir
~~~~~~~~~

.. code-block:: bash

    ipmcget -d serialdir

::

    Num           Source                  Destination
    0             PANEL COM               SYS COM

- COM口指向的是操作系统，而非IPMI

psuinfo
~~~~~~~

**PSU: Power Supply Unit**

.. code-block:: bash

    ipmcget -d psuinfo

::

    Current PSU Information :
    Slot   Manufacturer     Type                  SN                              Version                           Rated Power   InputMode
    1      HUAWEI           PAC900S12-B2          2102312XWKW0NC014123            DC:108 PFC:108                    900           AC
    2      HUAWEI           PAC900S12-B2          2102312XWKW0NC014244            DC:108 PFC:108                    900           AC

    Current PSU WorkMode    :
    Actual PSU Status       :
        Work Mode           : Load Balancing
    Predicted PSU Status    :
        Work Mode           : Load Balancing

    Hibernate Status        : Disabled

ipmcset
-------

::

    Usage: ipmcset [-t target] -d dataitem [-v value]
        -t <target>
           fru0                          Operate with fru0
           trap                          Operate SNMP trap
           service                       Operate with service
           user                          Operate with user
           maintenance                   Operate with maintenance
           sensor                        Operate with sensor
           securitybanner                Operate login security banner information
           syslog                        Operate syslog
           ntp                           Operate ntp
           vnc                           Operate vnc
           storage                       Configure storage device
           config                        Operate configuration
           vmm                           Operate virtual media
           certificate                   Operate certificate
           sol                           Operate SOL
           securityenhance               Operate security enhance
           precisealarm                  Operate with precise alarm

        -d <dataitem>
           fanmode                       Set fan mode,you can choose manual or auto
           fanlevel                      Set fan speed percent
           reset                         Reboot iBMC system
           identify                      Operate identify led
           upgrade                       Upgrade component
           clearcmos                     Clear CMOS
           bootdevice                    Set boot device
           shutdowntimeout               Set graceful shutdown timeout state and value
           frucontrol                    Fru control
           powerstate                    Set power state
           sel                           Clear SEL
           adduser                       Add user
           password                      Modify user password
           deluser                       Delete user
           privilege                     Set user privilege
           serialdir                     Set serial direction
           printscreen                   Print current screen to iBMC
           rollback                      Perform a manual rollback
           timezone                      Set time zone
           passwordcomplexity            Set password complexity check enable state
           ipaddr                        Set ip address
           backupipaddr                  Set backup ip address
           ipmode                        Set ip mode
           gateway                       Set gateway
           ipaddr6                       Set ipv6 address
           ipmode6                       Set ipv6 mode
           gateway6                      Set ipv6 gateway
           netmode                       Set net mode
           activeport                    Set EthGroup active port
           vlan                          Set sideband vlan
           restore                       Restore factory setting
           notimeout                     Set no timeout state
           emergencyuser                 Set emergency user
           autodiscovery                 Set autodiscovery configuration
           poweronpermit                 Set poweronpermit configuration
           minimumpasswordage            Set minimum password age configuration
           crl                           Upload CRL file
           psuworkmode                   Set PSU work mode
           clearlog                      Clear Log
           fpgagoldenfwrestore           FPGA golden firmware restore
           
-t <target>
~~~~~~~~~~~

-d <dataitem>
~~~~~~~~~~~~~

::

    createld                      Create a logical drive
    addld                         Add a logical drive on already existing disk array
    deleteld                      Delete a logical drive
    ldconfig                      Set logical drive configurations
    ctrlconfig                    Set RAID contoller configurations
    pdconfig                      Set physical drive configurations

ctreteld
""""""""

-v <RAID Controller ID>
^^^^^^^^^^^^^^^^^^^^^^^^^

**0**

::

    Error : missing option '-rl'.
    Usage:
      ipmcset -t storage -d createld -v <RAID Controller ID> -rl <r0|r1|r5|r6|r10|r50|r60> -pd <PD ID separated by commas>
                                     [-cachecade] [-sc <Span Count>] [-name <LD name>]  [-size <LD size>{m|g|t}] [-ss <64K|128K|256K|512K|1M>]
                                     [-rp <ra|nra>] [-wp <wt|wbwithbbu|wb>] [-iop <cio|dio>] [-ap <rw|ro|blocked>] [-dcp <enabled|disabled|default>]
                                     [-init <no|quick|full>]

    options:
      -v <RAID Controller ID>               The RAID controller on which logical drive will be created. It is mandatory.
      -rl <r0|r1|r5|r6|r10|r50|r60>         Logical drive RAID level. It is mandatory. When '-cachecade' is specified, RAID level 0/1 is valid.
          r0        =  RAID0
          r1        =  RAID1
          r5        =  RAID5
          r6        =  RAID6
          r10       =  RAID10
          r50       =  RAID50
          r60       =  RAID60

      -pd <PD ID separated by commas>       Physical drives ID participated in this logical drive, separated by commas. It is mandatory.
      -cachecade                            Logical drive is used for secondary cache. It is optional. It must be supported by RAID controller first.
      -sc <Span Count>                      Logical drive span count. 8 is maximum. It will be 1 on RAID0/1/5/6 and 2 on RAID10/50/60 by default.
                                            It is optional and not necessary when '-cachecade' is specified.
      -name <LD name>                       Logical drive name. 15 ASCII characters is maximum. It is optional.
                                            The value can't be same as the options if it starts with '-'.
      -size <LD size>{m|g|t}                The size of logical drive and the uint can be 'm'(megabytes) , 'g'(gigabytes) , 't'(terabytes).
                                            It is optional and not necessary when '-cachecade' is specified. If this option is not specified,
                                            the size of logical drive depends on the usable size of each physical drive.
      -ss <64K|128K|256K|512K|1M>           Logical drive strip size. The recommended range is 64K ~ 1M. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified and '-cachecade' is not specified, the default of strip size is '256K'.
                                            If this option is not specified but '-cachecade' is specified, the default of strip size is '1M'.
      -rp <ra|nra>                          Logical drive read policy. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified and '-cachecade' is not specified, the default of read policy is 'Read Ahead'.
                                            If this option is not specified but '-cachecade' is specified, the default of read policy is 'No Read Ahead'.
          ra        = Read ahead
          nra       = No Read ahead

      -wp <wt|wbwithbbu|wb>                 Logical drive write policy. It is optional. If this option is not specified, the default of
                                            write policy is 'Write Back with BBU'.
          wt        = Write through
          wbwithbbu = Write back with BBU
          wb        = Write back

      -iop <cio|dio>                        Logical drive IO policy. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified, the default of IO policy is 'Direct IO'.
          cio       = Cached IO
          dio       = Direct IO

      -ap <rw|ro|blocked>                   Logical drive access policy. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified, the default of access policy is 'Read Write'.
          rw        = Read write
          ro        = Read only
          blocked   = Blocked

      -dcp <enabled|disabled|default>       Logical drive disk cache policy. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified and '-cachecade' is not specified, the default of disk cache policy is 'Enabled'.
                                            If this option is not specified but '-cachecade' is specified, the default of disk cache policy is 'Disk's default'.
          enabled   = Enable disk cache
          disabled  = Disable disk cache
          default   = Unchanged and determined by disk type

      -init <no|quick|full>                 Logical drive init type. It is optional and not necessary when '-cachecade' is specified.
                                            If this option is not specified, the default of init type is 'None'.
          no        = Don't initialize the logical drive
          quick     = Quickly initialize the logical drive
          full      = Fully initialize the logical drive

    example:
        ipmcset -t storage -d createld -v 0 -rl r1 -pd 0,1 -name example -size 100.375g -ss 512k -rp ra -wp wb -ap rw -iop cio -dcp enabled -init quick

      or
        ipmcset -t storage -d createld -v 0 -rl r0 -pd 0,1,2 -name cachecade -cachecade -wp wb

-rl <r0|r1|r5|r6|r10|r50|r60>
###########################

::

    -rl <r0|r1|r5|r6|r10|r50|r60>         Logical drive RAID level. It is mandatory. When '-cachecade' is specified, RAID level 0/1 is valid.
    r0        =  RAID0
    r1        =  RAID1
    r5        =  RAID5
    r6        =  RAID6
    r10       =  RAID10
    r50       =  RAID50
    r60       =  RAID60

-pd <PD ID separated by commas>
##################################

**0&1**

-init <no|quick|full>
""""""""""""""""""""""""

::

    -init <no|quick|full>                 Logical drive init type. It is optional and not necessary when '-cachecade' is specified.
                                      If this option is not specified, the default of init type is 'None'.
    no        = Don't initialize the logical drive
    quick     = Quickly initialize the logical drive
    full      = Fully initialize the logical drive

.. code-block:: bash

    ipmcset -t storage -d createld -v 0 -rl r1 -pd 0,1 -init quick

::

    WARNING: The operation may have many adverse effects.
    Do you want to continue?[Y/N]:

::

    The operation may take a few seconds, Please wait...
    Create logical drive successfully. Logical drive ID is 239.

pdconfig
^^^^^^^^

::

    Usage:
        ipmcset -t storage -d pdconfig -v <Physical Drive ID>
                                       <[-state <online|offline|ug|jbod>] [-hotspare <none|global|dedicated|autoreplace> [-ld <Logical Drive ID>]]
                                        [-locate <start|stop>] [-cryptoerase] [-boot <none|primary|secondary|all>]>
        options:
          -v <Physical Drive ID>                The physical drive which will be set. It is mandatory.
          -state <online|offline|ug|jbod>       Set physical drive firmware state.
              online     = Set physical drive state to ONLINE. The drive must be participated in logical drive
              offline    = Set physical drive state to OFFLINE. The drive must be participated in logical drive
              ug         = Set physical drive state to UNCONFIGURED GOOD
              jbod       = Set physical drive state to JBOD (Drive is exposed and controlled by host). You should enable JBOD of RAID controller first

          -hotspare <none|global|dedicated|autoreplace>     Set physical drive hotspare state.
              none       = Cancel physical drive hot spare
              global     = Set physical drive as global hot spare device
              dedicated -ld <Logical Drive ID>     = Set physical drive as dedicated hot spare device and the option '-ld' specify
                                                     the logical drive ID for which physical drive dedicated hot spare, separated by commas.
              autoreplace -ld <Logical Drive ID>   = Set physical drive as autoreplace hot spare device and the option '-ld' specify
                                                     the logical drive ID for which physical drive autoreplace hot spare

          -locate <start|stop>                  Set physical drive location state.
              start      = Start locating physical drive
              stop       = Stop locating physical drive

          -cryptoerase                          Cryptographically erase physical drive.

          -boot                                 Set physical drive as boot device.
              none       = Disable physical drive as boot device
              primary    = Set physical drive as first boot device
              secondary  = Set physical drive as second boot device
              all        = Set physical drive as first and second boot device

        example:
            ipmcset -t storage -d pdconfig -v 1 -state ug

          or
            ipmcset -t storage -d pdconfig -v 1 -locate start

-v \<Physical Drive ID\>
""""""""""""""""""""""""

**0|1**

-state <online|offline|ug|jbod>
""""""""""""""""""""""""""""""""""

::

    -state <online|offline|ug|jbod>       Set physical drive firmware state.
    online     = Set physical drive state to ONLINE. The drive must be participated in logical drive
    offline    = Set physical drive state to OFFLINE. The drive must be participated in logical drive
    ug         = Set physical drive state to UNCONFIGURED GOOD
    jbod       = Set physical drive state to JBOD (Drive is exposed and controlled by host). You should enable JBOD of RAID controller first

.. code-block:: bash

    ipmcset -t storage -d pdconfig -v 0 -state ug

::

    WARNING: The operation may have many adverse effects.
    Do you want to continue?[Y/N]:

::

    The operation may take a few seconds, Please wait...
    Set physical drive state successfully.

user
~~~~

-d <dataitem>
----------------

::

    adduser                       Add user
    password                      Modify user password
    deluser                       Delete user
    privilege                     Set user privilege
    passwordcomplexity            Set password complexity check enable state
    emergencyuser                 Set emergency user
    lock                          Set user lock state
    unlock                        Set user unlock state
    addpublickey                  Add SSH public key
    delpublickey                  Delete SSH public key
    sshpasswordauthentication     Set SSH password authentication state
    interface                     Set user login interface
    usermgmtbyhost                Set user management function on the host side
    snmpprivacypassword           Set snmp privacy password
    weakpwddic                    Manage weak password dictionary
    state                         Enable/Disable user

adduser
^^^^^^^^

::

    Usage: ipmcset -d adduser -v <username>
        Contain any digits, letters, or characters except (:,\<>&"'/%) and space.
        User name's length is limitted to 1-16.
        User name cannot start with character "#" "+" or "-".
        User name cannot be just a dot (.) or two consecutive dots (..).

-v <username>
"""""""""""""""

.. code-block:: bash

    ipmcset -t user -d adduser -v huadi

- Input your password:
- Password:
- Confirm password:

::

    Add user successfully.

password
^^^^^^^^^
-v <username>
""""""""""""""

.. code-block:: bash
    
    ipmcset -t user -d password -v Administrator

- Input your password:
- Password:
- Confirm password:

::

    Set user password successfully.

privilege
^^^^^^^^^

::

    Usage: ipmcset -d privilege -v <username> <privilege>
    Privileges are:
        15       No Access
        2        User
        3        Operator
        4        Administrator
        5        Custom Role1
        6        Custom Role2
        7        Custom Role3
        8        Custom Role4

-v <username>
"""""""""""""

.. code-block:: bash

    ipmcset -t user -d privilege -v huadi 4

- Input your password: 
  
  - Set user privilege successfully.

ntp
^^^^

::

    -d <dataitem>
        status                        Set NTP enable status
        mode                          Set NTP mode
        preferredserver               Set preferred NTP server address
        alternativeserver             Set alternative NTP server address
        extraserver                   Set extra NTP server address
        authstatus                    Enable auth status
        groupkey                      Import NTP group key

-d <dataitem>
^^^^^^^^^^^^^

status
^^^^^^

-v <enabled|disabled>
"""""""""""""""""""""

Usage: ipmcset -t ntp -d status -v <enabled|disabled>

.. code-block:: bash

    ipmcset -t ntp -d status -v enabled

- 开启ntp

.. code-block:: bash

    Set NTP enable status (enabled) successfully.

mode
^^^^

Usage: ipmcset -t ntp -d mode -v <manual|dhcpv4|dhcpv6>

-v <manual|dhcpv4|dhcpv6>
#########################

.. code-block:: bash

    ipmcset -t ntp -d mode -v manual

- 设置ntp模式为手动

:: 

    Set NTP mode (manual) successfully.

preferredserver
^^^^^^^^^^^^^^^

Usage: ipmcset -t ntp -d preferredserver -v <addr>

-v <addr>
#########

::

    ipmcset -t ntp -d preferredserver -v 172.21.66.13

::

    Set NTP preferred server (172.21.66.13) successfully.

-d <dataitem>
~~~~~~~~~~~~~

::

    -d <dataitem>
        fanmode                       Set fan mode,you can choose manual or auto
        fanlevel                      Set fan speed percent
        reset                         Reboot iBMC system
        identify                      Operate identify led
        upgrade                       Upgrade component
        clearcmos                     Clear CMOS
        bootdevice                    Set boot device
        shutdowntimeout               Set graceful shutdown timeout state and value
        frucontrol                    Fru control
        powerstate                    Set power state
        sel                           Clear SEL
        adduser                       Add user
        password                      Modify user password
        deluser                       Delete user
        privilege                     Set user privilege
        serialdir                     Set serial direction
        printscreen                   Print current screen to iBMC
        rollback                      Perform a manual rollback
        timezone                      Set time zone
        passwordcomplexity            Set password complexity check enable state
        ipaddr                        Set ip address
        backupipaddr                  Set backup ip address
        ipmode                        Set ip mode
        gateway                       Set gateway
        ipaddr6                       Set ipv6 address
        ipmode6                       Set ipv6 mode
        gateway6                      Set ipv6 gateway
        netmode                       Set net mode
        activeport                    Set EthGroup active port
        vlan                          Set sideband vlan
        restore                       Restore factory setting
        notimeout                     Set no timeout state
        emergencyuser                 Set emergency user
        autodiscovery                 Set autodiscovery configuration
        poweronpermit                 Set poweronpermit configuration
        minimumpasswordage            Set minimum password age configuration
        crl                           Upload CRL file
        psuworkmode                   Set PSU work mode
        clearlog                      Clear Log
        fpgagoldenfwrestore           FPGA golden firmware restore

timezone
~~~~~~~~

::

    Usage: ipmcset -d timezone -v <timezone>
    Options are:
            Time-Offset: -12:00~+14:00            e.g. +08:00,-04:30
                         UTC-12:00~UTC+14:00      e.g. UTC+08:00,UTC-04:30
                         GMT-12:00~GMT+14:00      e.g. GMT+08:00,GMT-04:30
            Timezone   : <City Name>              e.g. Asia/Shanghai,America/New_York

-v <timezone>
^^^^^^^^^^^^^

.. code-block:: bash

    ipmcset -d timezone -v utc+08:00

- 不区分大小写，``+%H:M``

::

    Set time zone successfully.

ipmode
~~~~~~

Usage: ipmcset -d ipmode -v <dhcp|static>

-v <dhcp|static>
^^^^^^^^^^^^^^^^

.. code-block:: bash

    ipmcset -d ipmode -v static
    # Set static mode successfully.

gateway
~~~~~~~

Usage: ipmcset -d gateway -v <gateway>

-v <gateway>
^^^^^^^^^^^^

.. code-block:: bash

    ipmcset -d gateway -v 172.21.31.254
    # Set GATEWAY successfully.

ipaddr
~~~~~~

Usage: ipmcset -d ipaddr -v <ipaddr> <mask> [gateway]

-v <ipaddr> <mask> [gateway]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

    ipmcset -d ipaddr -v 172.21.27.69 255.255.248.0 172.21.31.254
    # Set IP address successfully.
    # Set MASK address successfully.
    # Set GATEWAY successfully.

df
--

--help
~~~~~~

::

    BusyBox v1.32.1 (2022-11-15 02:15:00 CST) multi-call binary.

    Usage: df [-PkmhTai] [-B SIZE] [FILESYSTEM]...

    Print filesystem usage statistics

            -P      POSIX output format
            -k      1024-byte blocks (default)
            -m      1M-byte blocks
            -h      Human readable (e.g. 1K 243M 2G)
            -T      Print filesystem type
            -a      Show all filesystems
            -i      Inodes
            -B SIZE Blocksize


route
-----

help
~~~~

::

    Usage: route [option]

    Check kernel routing tables

    Options:
            -n                Don't resolve names
            -e                Display other/more information
            -A inet{6}        Select address family

netstat
-------

help
~~~~

::

    BusyBox v1.32.1 (2022-11-15 02:15:00 CST) multi-call binary.

    Usage: netstat [-ral] [-tuwx] [-enWp]
    
    Display networking information
    
            -r      Routing table
            -a      All sockets
            -l      Listening sockets
                    Else: connected sockets
            -t      TCP sockets
            -u      UDP sockets
            -w      Raw sockets
            -x      Unix sockets
                    Else: all socket types
            -e      Other/more information
            -n      Don't resolve names
            -W      Wide display
            -p      Show PID/program name for sockets



