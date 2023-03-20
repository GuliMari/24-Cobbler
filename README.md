# ДЗ: автоматизировать процесс установки Cobbler cледуя шагам из документа https://cobbler.github.io/quickstart/.

# Выполнение
Поднимаем 2 виртуалки: `cobbler` с настроенным cobbler и `client`.
Заходим на сервер `cobbler` через веб-интерфейс:

![Image alt](https://github.com/GuliMari/24-Cobbler/blob/main/cobbler_system.png)

Смотрим инфо о смонтированном образе:

```bash
[root@cobbler ~]# cobbler distro report --name=CentOS-7-x86_64
Name                           : CentOS-7-x86_64
Architecture                   : x86_64
TFTP Boot Files                : {}
Breed                          : redhat
Comment                        : 
Fetchable Files                : {}
Initrd                         : /var/www/cobbler/ks_mirror/CentOS-7-x86_64/images/pxeboot/initrd.img
Kernel                         : /var/www/cobbler/ks_mirror/CentOS-7-x86_64/images/pxeboot/vmlinuz
Kernel Options                 : {}
Kernel Options (Post Install)  : {}
Kickstart Metadata             : {'tree': 'http://@@http_server@@/cblr/links/CentOS-7-x86_64'}
Management Classes             : []
OS Version                     : rhel7
Owners                         : ['admin']
Red Hat Management Key         : <<inherit>>
Red Hat Management Server      : <<inherit>>
Template Files                 : {}
```

Инфо о системе:

```bash
[root@cobbler ~]# cobbler distro report --name=CentOS-7-x86_64
Name                           : CentOS-7-x86_64
Architecture                   : x86_64
TFTP Boot Files                : {}
Breed                          : redhat
Comment                        : 
Fetchable Files                : {}
Initrd                         : /var/www/cobbler/ks_mirror/CentOS-7-x86_64/images/pxeboot/initrd.img
Kernel                         : /var/www/cobbler/ks_mirror/CentOS-7-x86_64/images/pxeboot/vmlinuz
Kernel Options                 : {}
Kernel Options (Post Install)  : {}
Kickstart Metadata             : {'tree': 'http://@@http_server@@/cblr/links/CentOS-7-x86_64'}
Management Classes             : []
OS Version                     : rhel7
Owners                         : ['admin']
Red Hat Management Key         : <<inherit>>
Red Hat Management Server      : <<inherit>>
Template Files                 : {}

[root@cobbler ~]# cobbler system list
   centos7
[root@cobbler ~]# cobbler system report --name=centos7
Name                           : centos7
TFTP Boot Files                : {}
Comment                        : 
Enable gPXE?                   : <<inherit>>
Fetchable Files                : {}
Gateway                        : 
Hostname                       : 
Image                          : 
IPv6 Autoconfiguration         : False
IPv6 Default Device            : 
Kernel Options                 : {}
Kernel Options (Post Install)  : {}
Kickstart                      : /var/lib/cobbler/kickstarts/ks.cfg
Kickstart Metadata             : {}
LDAP Enabled                   : False
LDAP Management Type           : authconfig
Management Classes             : <<inherit>>
Management Parameters          : <<inherit>>
Monit Enabled                  : False
Name Servers                   : []
Name Servers Search Path       : []
Netboot Enabled                : True
Owners                         : <<inherit>>
Power Management Address       : 
Power Management ID            : 
Power Management Password      : 
Power Management Type          : ipmitool
Power Management Username      : 
Profile                        : CentOS-7-x86_64
Internal proxy                 : <<inherit>>
Red Hat Management Key         : <<inherit>>
Red Hat Management Server      : <<inherit>>
Repos Enabled                  : False
Server Override                : <<inherit>>
Status                         : production
Template Files                 : {}
Virt Auto Boot                 : <<inherit>>
Virt CPUs                      : <<inherit>>
Virt Disk Driver Type          : <<inherit>>
Virt File Size(GB)             : <<inherit>>
Virt Path                      : <<inherit>>
Virt PXE Boot                  : 0
Virt RAM (MB)                  : <<inherit>>
Virt Type                      : <<inherit>>
```

Запускаем клиент и выбираем в появившемся меню `CentOS7`, после чего начнется автозагрузка:

![Image alt](https://github.com/GuliMari/24-Cobbler/blob/main/menu.png)

![Image alt](https://github.com/GuliMari/24-Cobbler/blob/main/%D0%B0%D0%B2%D1%82%D0%BE%D0%B7%D0%B0%D0%B3%D1%80%D1%83%D0%B7%D0%BA%D0%B0.png)
