# zookeeper-releases
* 本文是 ZooKeeper 的快速搭建,旨在帮助大家以最快的速度完成一个 ZK  集群的搭建,以便开展其它工作。本方不包含多余说明及任何调优方面的高级配置。如果要 进行更深一层次的配置,请移步《ZooKeeper 管理员指南——部署与运维》。
单机模式(7 步)

* Step1:配置 JAVA 环境。检验方法:执行 java –version 和 javac –version 命令。
* Step2:下载并解压 zookeeper。 链接:http://mirror.bjtu.edu.cn/apache/zookeeper/zookeeper-3.4.3/,(更多版本:http://dwz.cn/37HGI)
* 最终生成目录类似结构:/home/admin/taokeeper/zookeeper-3.4.3/bin Step3:重命名 zoo_sample.cfg 文件
Step4:vi zoo.cfg,修改
* Step5:创建数据目录:mkdir /home/admin/taokeeper/zookeeper-3.4.3/data Step6:启动 zookeeper:执行
* Step7:检测是否成功启动:执行
  
     mv /home/admin/taokeeper/zookeeper-3.4.3/conf/zoo_sample.cfg zoo.cfg
     dataDir=/home/admin/taokeeper/zookeeper-3.4.3/data
     mkdir /home/admin/taokeeper/zookeeper-3.4.3/data
    /home/admin/taokeeper/zookeeper-3.4.3/bin/zkServer.sh start
    /home/admin/taokeeper/zookeeper-3.4.3/bin/zkCli.sh
或
     echo stat|nc localhost 2181
    1/ 3
     集群模式(8 步)
* Step1:配置 JAVA 环境。检验方法:执行 java –version 和 javac –version 命令。
* Step2:下载并解压 zookeeper。 链接:http://mirror.bjtu.edu.cn/apache/zookeeper/zookeeper-3.4.3/,(更多版本:http://dwz.cn/37HGI)

* 最终生成目录类似结构:<font color=#DC143C>/home/admin/taokeeper/zookeeper-3.4.3/bin </font>
* Step3:重命名 zoo_sample.cfg 文件
* Step4:vi zoo.cfg,修改
 这里要注意下 server.1 这个后缀,表示的是 1.2.3.4 这个机器,在机器中的 server id 是 1
* Step5:创建数据目录:mkdir /home/admin/taokeeper/zookeeper-3.4.3/data Step6:在标识 Server ID.
在/home/admin/taokeeper/zookeeper-3.4.3/data 目录中创建文件 myid 文件,每个文件中分别写入当前机器的 server id,例如 1.2.3.4 这个机器,在 /home/admin/taokeeper/zookeeper-3.4.3/data 目录的 myid 文件中写入数字 1.
* Step7:启动 zookeeper:执行 Step8:检测是否成功启动:执行
  
mv /home/admin/taokeeper/zookeeper-3.4.3/conf/zoo_sample.cfg zoo.cfg
dataDir=/home/admin/taokeeper/zookeeper-3.4.3/data server.1=1.2.3.4:2888:3888 server.2=1.2.3.5:2888:3888 server.3=1.2.3.6:2888:3888
 mkdir /home/admin/taokeeper/zookeeper-3.4.3/data
 /home/admin/taokeeper/zookeeper-3.4.3/bin/zkServer.sh start
/home/admin/taokeeper/zookeeper-3.4.3/bin/zkCli.sh
或
echo stat|nc localhost 2181
