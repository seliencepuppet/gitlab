# Gitlab

<br/>

gitlab目前最好的安装环境是在 centos7版本系统上面，下面记录安装过程和方法。

```shell
[root@zhangyz ~]# curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | bash
Resolving Dependencies
--> Running transaction check
---> Package yum-utils.noarch 0:1.1.30-37.el6 will be updated
---> Package yum-utils.noarch 0:1.1.30-42.el6_10 will be an update
--> Processing Dependency: yum >= 3.2.29-77 for package: yum-utils-1.1.30-42.el6_10.noarch
--> Running transaction check
---> Package yum.noarch 0:3.2.29-73.el6.centos will be updated
---> Package yum.noarch 0:3.2.29-81.el6.centos.0.1 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================================================================================================================================
 Package                                                    Arch                                                    Version                                                                      Repository                                                Size
================================================================================================================================================================================================================================================================
Updating:
 yum-utils                                                  noarch                                                  1.1.30-42.el6_10                                                             updates                                                  114 k
Updating for dependencies:
 yum                                                        noarch                                                  3.2.29-81.el6.centos.0.1                                                     updates                                                  1.0 M

Transaction Summary
================================================================================================================================================================================================================================================================
Upgrade       2 Package(s)

Total download size: 1.1 M
Downloading Packages:
(1/2): yum-3.2.29-81.el6.centos.0.1.noarch.rpm                                                                                                                                                                                           | 1.0 MB     00:00     
(2/2): yum-utils-1.1.30-42.el6_10.noarch.rpm                                                                                                                                                                                             | 114 kB     00:00     
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                                                                                           2.7 MB/s | 1.1 MB     00:00     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Updating   : yum-3.2.29-81.el6.centos.0.1.noarch                                                                                                                                                                                                          1/4 
  Updating   : yum-utils-1.1.30-42.el6_10.noarch                                                                                                                                                                                                            2/4 
  Cleanup    : yum-utils-1.1.30-37.el6.noarch                                                                                                                                                                                                               3/4 
  Cleanup    : yum-3.2.29-73.el6.centos.noarch                                                                                                                                                                                                              4/4 
  Verifying  : yum-utils-1.1.30-42.el6_10.noarch                                                                                                                                                                                                            1/4 
  Verifying  : yum-3.2.29-81.el6.centos.0.1.noarch                                                                                                                                                                                                          2/4 
  Verifying  : yum-3.2.29-73.el6.centos.noarch                                                                                                                                                                                                              3/4 
  Verifying  : yum-utils-1.1.30-37.el6.noarch                                                                                                                                                                                                               4/4 

Updated:
  yum-utils.noarch 0:1.1.30-42.el6_10                                                                                                                                                                                                                           

Dependency Updated:
  yum.noarch 0:3.2.29-81.el6.centos.0.1                                                                                                                                                                                                                         

Complete!
Generating yum cache for gitlab_gitlab-ce...
Importing GPG key 0xE15E78F4:
 Userid: "GitLab B.V. (package repository signing key) <packages@gitlab.com>"
 From  : https://packages.gitlab.com/gitlab/gitlab-ce/gpgkey

The repository is setup! You can now install packages.
```

