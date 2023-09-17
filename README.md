Update kernel Centos 7


[root@kernel-update-Centos ~]#  uname -sr
Linux 3.10.0-957.12.2.el7.x86_64


[root@kernel-update-Centos ~]# yum search redis
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: it1.mirror.vhosting-it.com
 * extras: it1.mirror.vhosting-it.com
 * updates: it1.mirror.vhosting-it.com
base                                                                 | 3.6 kB  00:00:00     
extras                                                               | 2.9 kB  00:00:00     
updates                                                              | 2.9 kB  00:00:00     
(1/4): base/7/x86_64/group_gz                                        | 153 kB  00:00:00     
(2/4): extras/7/x86_64/primary_db                                    | 250 kB  00:00:00     
(3/4): updates/7/x86_64/primary_db                                   |  22 MB  00:00:06     
(4/4): base/7/x86_64/primary_db                                      | 6.1 MB  00:00:07     
==================================== N/S matched: redis ====================================
pcp-pmda-redis.x86_64 : Performance Co-Pilot (PCP) metrics for Redis

  Name and summary matches only, use "search all" for everything.


[root@kernel-update-Centos ~]# rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org


[root@kernel-update-Centos ~]# rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-5.el7.elrepo.noarch.rpm
Retrieving http://www.elrepo.org/elrepo-release-7.0-5.el7.elrepo.noarch.rpm
Preparing...                          ################################# [100%]
Updating / installing...
   1:elrepo-release-7.0-5.el7.elrepo  ################################# [100%]
[root@kernel-update-Centos ~]# yum --disablerepo="*" --enablerepo="elrepo-kernel" list available
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * elrepo-kernel: ftp.cc.uoc.gr
elrepo-kernel                                                        | 3.0 kB  00:00:00     
elrepo-kernel/primary_db                                             | 2.1 MB  00:00:01     
Available Packages
elrepo-release.noarch                         7.0-6.el7.elrepo                 elrepo-kernel
kernel-lt.x86_64                              5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-devel.x86_64                        5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-doc.noarch                          5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-headers.x86_64                      5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-tools.x86_64                        5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-tools-libs.x86_64                   5.4.256-1.el7.elrepo             elrepo-kernel
kernel-lt-tools-libs-devel.x86_64             5.4.256-1.el7.elrepo             elrepo-kernel
kernel-ml.x86_64                              6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-devel.x86_64                        6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-doc.noarch                          6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-headers.x86_64                      6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-tools.x86_64                        6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-tools-libs.x86_64                   6.5.3-1.el7.elrepo               elrepo-kernel
kernel-ml-tools-libs-devel.x86_64             6.5.3-1.el7.elrepo               elrepo-kernel
perf.x86_64                                   5.4.256-1.el7.elrepo             elrepo-kernel
python-perf.x86_64                            5.4.256-1.el7.elrepo             elrepo-kernel



[root@kernel-update-Centos ~]# yum --enablerepo=elrepo-kernel install kernel-ml
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.mirror.garr.it
 * elrepo: mirror.koddos.net
 * elrepo-kernel: mirror.koddos.net
 * extras: centos.mirror.garr.it
 * updates: centos.mirror.garr.it
elrepo                                                               | 3.0 kB  00:00:00     
elrepo/primary_db                                                    | 356 kB  00:00:00     
Resolving Dependencies
--> Running transaction check
---> Package kernel-ml.x86_64 0:6.5.3-1.el7.elrepo will be installed
--> Finished Dependency Resolution

Dependencies Resolved

============================================================================================
 Package           Arch           Version                       Repository             Size
============================================================================================
Installing:
 kernel-ml         x86_64         6.5.3-1.el7.elrepo            elrepo-kernel          67 M

Transaction Summary
============================================================================================
Install  1 Package

Total download size: 67 M
Installed size: 343 M
Is this ok [y/d/N]: y
Downloading packages:
kernel-ml-6.5.3-1.el7.elrepo.x86_64.rpm                              |  67 MB  00:00:14     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Warning: RPMDB altered outside of yum.
  Installing : kernel-ml-6.5.3-1.el7.elrepo.x86_64                                      1/1
  Verifying  : kernel-ml-6.5.3-1.el7.elrepo.x86_64                                      1/1

Installed:
  kernel-ml.x86_64 0:6.5.3-1.el7.elrepo                                                     

Complete!

reboot

[root@kernel-update-Centos ~]#  uname -sr
Linux 6.5.3-1.el7.elrepo.x86_64


[root@kernel-update-Centos ~]# sudo grub2-set-default 0
[root@kernel-update-Centos ~]#

reboot

[root@kernel-update-Centos ~]#  uname -sr
Linux 6.5.3-1.el7.elrepo.x86_64
