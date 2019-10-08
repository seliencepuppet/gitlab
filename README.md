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

<br/>

接下来执行安装命令, 一键

```shell
[root@zhangyz ~]# yum -y install gitlab-ce
......
```

### 接下来编辑 /etc/gitlab/gitlab.rb 这个配置文件更改一些选项

<br/>

#### 01.更改访问的url地址
```shell
[root@zhangyz ~]# vim /etc/gitlab/gitlab.rb
13 external_url 'http://192.168.152.128'
```

#### 02.给root用户设置密码方便登录web管理界面

```shell
[root@zhangyz ~]# gitlab-rails console production
-------------------------------------------------------------------------------------
 GitLab:       11.10.4 (62c464651d2)
 GitLab Shell: 9.0.0
 PostgreSQL:   9.6.11
-------------------------------------------------------------------------------------
Loading production environment (Rails 5.0.7.2)
irb(main):001:0> u=User.where(id:1).first
=> #<User id:1 @root>
irb(main):002:0> u=User.all
=> #<ActiveRecord::Relation [#<User id:1 @root>]>
irb(main):003:0> 
irb(main):004:0> u=User.where(id:1).first
=> #<User id:1 @root>
irb(main):005:0> u.password='12345678'
=> "12345678"
irb(main):006:0> u.password_confirmation='12345678'
=> "12345678"
irb(main):007:0> u.save
Enqueued ActionMailer::DeliveryJob (Job ID: d878cd2b-321d-4b4c-b9b2-13577e088f2f) to Sidekiq(mailers) with arguments: "DeviseMailer", "password_change", "deliver_now", #<GlobalID:0x00007f4e01ba46d0 @uri=#<URI::GID gid://gitlab/User/1>>
=> true
irb(main):010:0> 
irb(main):011:0> u=User.where(id:1).first
=> #<User id:1 @root>
irb(main):012:0> 
irb(main):013:0> exit
```
