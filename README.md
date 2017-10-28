# TNoS
TensorFlowOnSpark learn

Linux 下升级python和安装pip 
http://www.cnblogs.com/Edwardzhao/p/5856924.html

ssh localhost
ssh连接时提示THE AUTHENTICITY OF HOST XX CAN’T BE ESTABLISHED
http://www.cnblogs.com/gauze/p/5554840.html
修改好配置后，重新启动sshd服务即可，命令为：/etc/init.d/sshd restart （或 service sshd restart ）

hadoop安装(ha/2.8)
http://blog.csdn.net/happy_wu/article/details/70240014
scp jdk.tar.gz sk2@sk2:download
scp -r hadoop/ sk2@sk2:common/hadoop-2.8.1/etc
sk1@sk2's password: sk1: starting namenode, 
由于Hadoop要求所有机器上Hadoop的部署目录结构要求相同（因为在启动时按与主节点相同的目录启动其它任务节点），并且都有一个相同的用户名账户。参考各种文档上说的是所有机器都建立一个hadoop用户，使用这个账户来实现无密码认证。 

zk安装

关闭防火墙
systemctl stop firewalld.service #停止firewall
systemctl disable firewalld.service #禁止firewall开机启动
firewall-cmd --state #查看默认防火墙状态（关闭后显示notrunning，开启后显示running）
关闭SELinux
vi /etc/selinux/config  
SELINUX=disabled 

Permission denied (publickey,gssapi-keyex,gssapi-with-mic)
http://www.cnblogs.com/xubing-613/p/6844564.html
PasswordAuthentication"参数值为"no",修改回"yes"



1).在datanode的三个节点(datanode01,datanode02,datanode02)上启动journalnode
   sbin/hadoop-daemon.sh start journalnode
   启动zk集群
2).格式化HDFS 
  在namenode01执行
    bin/hdfs namenode -format
    sbin/hadoop-daemon.sh start namenode
  在namenode02执行 
    bin/hdfs namenode -bootstrapStandby
  在namenode01执行
    sbin/hadoop-daemon.sh stop namenode
3).格式化ZKFS 
  在namenode01执行:
    bin/hdfs zkfc -formatZK
4).启动HDFS: 
  在namenode01执行:
    sbin/start-dfs.sh    
5)格式化后数据一致：
  
