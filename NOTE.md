# 安装常用的开发软件
用于介绍一些常用开发软件的安装

## 在Windows中安装JDK（解压版本）

### 下载免安装版JDK

到如下网址下载:

```tex
https://adoptium.net/zh-CN/temurin/releases/
```

然后找个位置，例如D盘，执行解压，此时解压后的位置为:

```tex
 D:\Java\jdk8u362-b09
```

然后新增环境变量CLASSPATH:

```tex
.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
```

在PATH中新增:

```tex
PATH: %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin
```

## 在Windows中安装JDK（exe安装版）

### 建立安装文件夹
在D盘，或者其他盘，建立安装JDK的文件的位置:

- JDK的安装位置
```tex
 D:\Java\Jdk
```

- JRE的安装位置
```tex
 D:\Java\Jre
```
**然后执行安装即可**

### 在系统变量下面配置下面的变量
安装的JDK路径:
```
JAVA_HOME: D:\Java\Jdk
```
CLASSPATH:
```
.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
```
PATH:
```
PATH: %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin
```
#### 需要注意的事项
- Jdk和Jre
 **在Win解压安装的过程中，第一个是安装Jdk，第二个是安装Jre，此时应该选择在不同的地方一般为:** 
```
D:\Java\Jdk 以及 D:\Java\Jre
```
  **注意:如果是Win10的话，需要在PATH和CLASSPATH路径上面写上绝对路径。win10和其他的不同就出来了，win的path变量，要用jdk的绝对路径，而不能用%JAVA_HOME%这一类的，计算机识别不了。** 
  **此时CLASSPATH和PATH的路径应该写为:** 
- CLASSPATH:
```
.;D:\Java\Jdk\lib;D:\Java\Jdk\lib\dt.jar;D:\Java\Jdk\lib\tools.jar (记住不要忘记最前面的.)
```
- PATH:
```
D:\Java\Jdk\bin
```

## 安装NodeJS

### 1,Win配置Node环境

把NodeJS压缩包解压到D盘的NodeJS文件夹下（也可以是其他文件夹）

#### 新建一个系统变量
变量名：
```
NODE_HOME
```
变量值（你的安装目录）：
```
D:\NodeJS
```
#### 编辑path变量，新增2条变量
```
%NODE_HOME%\Node
%NODE_HOME%\node_global
```
#### 打开git bash窗口，运行下面的命令
```
node -v
```
#### 设置环境node的缓存路径
```
#mac:
npm config set prefix "/Users/singer/NodeJS/node_global"
npm config set cache "/Users/singer/NodeJS/node_cache"
#win:
npm config set prefix "D:\NodeJS\node_global"
npm config set cache "D:\NodeJS\node_cache"
```
#### npm配置源和sass_binary_site的源
```
npm config set registry https://registry.npmmirror.com/ && npm config set sass_binary_site https://npmmirror.com/mirrors/node-sass
npm config get registry
```
#### 安装Yarn

```
npm install yarn -g
```

#### yarn设置yarn源和sass_binary_site的源

```
yarn config set registry https://registry.npmmirror.com/ && yarn config set sass_binary_site   https://npmmirror.com/mirrors/node-sass
yarn config get registry
```
#### 设置scripts-prepend-node-path
```
npm config set scripts-prepend-node-path true
```
#### 设置忽略yarn在构建的时候忽略NodeJS版本信息
```
yarn config set ignore-engines true
```

### 2,Mac配置Node环境变量

#### 如果是pkg包安装
1. 查看npm全局包可执行文件路径
```
npm -g bin
```

2. 编辑环境变量配置文件
```
vim ~/.bash_profile
```

3. 在最下面输入 npm -g bin 输出的信息(如/usr/local/bin/)
```
PATH=$PATH:/Users/singer/NodeJS/Node/bin
```

4. 最后执行source
```
source ~/.bash_profile
```

#### 如果是解压包安装
- 直接下载二进制包
```
wget https://cdn.npmmirror.com/binaries/node/v14.19.1/node-v14.19.1-darwin-x64.tar.gz
```

- 新建NodeJS相关文件夹
```
mkdir NodeJS
cd NodeJS
mkdir node_cache
mkdir node_global
mkdir Node
```
**上面文件夹的含义:**

|   文件夹    |             含义             |      备注      |
| :---------: | :--------------------------: | :------------: |
|   NodeJS    | NodeJS所有安装文件及其缓存库 |                |
| node_cache  |        NodeJS缓存文件        |                |
| node_global |        NodeJS全局文件        |                |
|    Node     |        NodeJS主包文件        | 主要的包的文件 |


- 解压二进制安装包
 将第一步下载下来的二进制包，解压到NodeJS/Node
```
mv node/v14.19.1/node-v14.19.1-darwin-x64.tar.gz  ~/NodeJS/Node
tar -zxvf node-v14.19.1-darwin-x64.tar.gz 
```

- 配置NodeJS环境变量
编辑 ~/.bash_profile 文件:
```
sudo vim ~/.bash_profile
```
在最后一行新增Node文件夹的位置:
```
PATH=$PATH:/Users/singer/NodeJS/Node/bin
```
让刚才的修改生效**(临时)**
```
source ~/.bash_profile
```
让刚才的修改**永久生效**
```
vim ~/.zshrc
#在最后一行添加
source ~/.bash_profile
```

#### 进行一些额外的设置
```
#mac:
npm config set prefix "/Users/singer/NodeJS/node_global"
npm config set cache "/Users/singer/NodeJS/node_cache"
#win:
npm config set prefix "D:\NodeJS\node_global"
npm config set cache "D:\NodeJS\node_cache"
#npm配置源和sass_binary_site的源
npm config set registry https://registry.npmmirror.com && npm config set sass_binary_site https://npmmirror.com/mirrors/node-sass
npm config get registry
#yarn设置yarn源和sass_binary_site的源
yarn config set registry https://registry.npmmirror.com && yarn config set sass_binary_site https://npmmirror.com/mirrors/node-sass
```

升级方法

```
#清理npm的缓存
npm cache clean -f
#升级node和npm到最新版本
#第一步，先查看本机node.js版本:
node -v
#第二步，清除node.js的cache：
sudo npm cache clean -f
#第三步，安装 n 工具，这个工具是专门用来管理node.js版本的，别怀疑这个工具的名字，是他是他就是他，他的名字就是 #"n"
sudo npm install -g n
#第四步，安装最新版本的node.js
sudo n stable
#第五步，再次查看本机的node.js版本：
node -v
#第六步，更新npm到最新版：
sudo npm install npm@latest -g
#安装VUE路由
cnpm install vue-router --save
#全局安装express模块  
npm install -g express  
#npm安装yarn
npm install -g yarn
#npm升级yarn到最新版本
npm install yarn@latest -g
```

#### IDEA的垃圾回收配置

```
-Xms256m
-Xmx1024m
-XX:ReservedCodeCacheSize=512m
-XX:+UseG1GC
-XX:MaxGCPauseMillis=100
-XX:InitiatingHeapOccupancyPercent=20

-XX:G1HeapRegionSize=32m
-XX:SoftRefLRUPolicyMSPerMB=0
-XX:CICompilerCount=4
-XX:G1HeapWastePercent=0
-XX:+HeapDumpOnOutOfMemoryError
-XX:-OmitStackTraceInFastThrow
-ea
-Dsun.io.useCanonCaches=false
-Djdk.http.auth.tunneling.disabledSchemes=""
-Djdk.attach.allowAttachSelf=true
-Djdk.module.illegalAccess.silent=true
-Dkotlinx.coroutines.debug=off
-XX:ErrorFile=$USER_HOME/java_error_in_idea_%p.log
-XX:HeapDumpPath=$USER_HOME/java_error_in_idea.hprof

--add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
--add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
-javaagent:D:\IntelliJ-IDEA-2022.3.3\jetbra\ja-netfilter.jar=jetbrains

-XX:+PrintGC
-XX:+UseGCLogFileRotation
-XX:NumberOfGCLogFiles=10
-XX:GCLogFileSize=20M
-XX:+G1SummarizeConcMark
-XX:+G1PrintHeapRegions
-XX:+G1TraceEagerReclaimHumongousObjects
-XX:G1PrintRegionLivenessInfo
-XX:+G1SummarizeRSetStats
-XX:+PrintGCDetails
-XX:+PrintGCDateStamps
-XX:+PrintGCTimeStamps
-XX:+PrintHeapAtGC
-XX:+TraceClassUnloading
-XX:+PrintCompilation
-XX:+CITime
-Xloggc:$USER_HOME/IntelliJ-IDEA-GC-%t.log

```

## G1垃圾回收配置

```shell
#!/usr/bin/env bash


#JDK路径
#JAVA_HOME=""

#利用pwd命令拿到当前工程目录，实际拿到到的是该shell脚本的目录。再利用sed命令将/bin替换为空
Project_HOME=$(echo `pwd` | sed 's/\/sbin//')

LOG_DIR=$Project_HOME/logs
APPLICATION_MAIN=cn.common.AnimalWebApplication
CLASSPATH=$Project_HOME/classes


PORT=9007
DEBUG_PORT=8007 #调试端口

#EVN=development
#EVN=default
#EVN=production
#EVN=dev
EVN=$1


#JVM启动参数
#-server:一定要作为第一个参数,在多个CPU时性能佳
#-Xloggc:记录GC日志,这里建议写成绝对路径,如此便可在任意目录下执行该shell脚本
#JAVA_OPTS="-ms512m -mx512m -Xmn256m -Djava.awt.headless=true -XX:MaxPermSize=128m"
#JAVA_OPTS="-Dspring.profiles.active=$EVN -Dserver.port=$PORT -Duser.timezone=GMT+8 -server -Xms256m -Xmx512m -Xloggc:${LOG_DIR}/gc.log"
#-XX:PermSize=256M JVM初始分配的非堆内存 -XX:MaxPermSize=2048M JVM最大允许分配的非堆内存，按需分配
#上面的配置在Java8里面使用-XX:MetaspaceSize=200m -XX:MaxMetaspaceSize=256m代替
#-XX:MaxNewSize=1024m 最大的新生代的内存
#禁止代码中显式调用GC (System.gc()无效)
#使用并发标记清除（CMS）收集器UseConcMarkSweepGC
#降低标记停顿CMSParallelRemarkEnabled
#原始类型的快速优化 UseFastAccessorMethods
#-XX:LargePageSizeInBytes  指定 Java heap 的分页页面大小
#UseCMSInitiatingOccupancyOnly  使用手动定义的初始化定义开始CMS收集
#CMSInitiatingOccupancyFraction 使用cms作为垃圾回收使用70％后开始CMS收集
#-Xss规定了每个线程堆栈的大小。一般情况下256K是足够了。影响了此进程中并发线程数大小。
#-XX:+AggressiveHeap 使用大量的物理内存,长时间大内存使用的优化，能检查计算资源（内存， 处理器数量）,至少需要256MB内存,大量的CPU／内存
#-XX:CMSInitiatingOccupancyFraction=70代表CMS在对内存占用率达到70%的时候开始GC(因为CMS会有浮动垃圾,所以一般都较早启动GC)
#-XX:+UseCMSInitiatingOccupancyOnly 设定的回收阈值(上面指定的70%),如果不指定,JVM仅在第一次使用设定值,后续则自动调整
#-XX:+CMSScavengeBeforeRemark在CMS GC前启动一次ygc，目的在于减少old gen对ygc gen的引用，降低remark时的开销-----因为CMS的GC耗时 80%都在remark阶段
#-XX:+UseAdaptiveSizePolicy 自动选择年轻代区大小和相应的Survivor区比例
#-XX:+UseParallelOldGC 年老代垃圾收集方式为并行收集(Parallel Compacting)
#-XX:ParallelGCThreads 并行收集器的线程数此值最好配置与处理器数目相等 同样适用于CMS
#-XX:+UseParallelGC 择垃圾收集器为并行收集器.此配置仅对年轻代有效.即上述配置下,年轻代使用并发收集,而年老代仍旧使用串行收集
#-XX:+UseParNewGC 设置年轻代为并行收集 JDK5以上会自动设置,所以无需配置
#-XX:+UseFastAccessorMethods 原始类型的快速优化 -XX:+AggressiveOpts 快速编译 -XX:+UseBiasedLocking 锁机制的性能改善
#-XX:+DisableExplicitGC 禁止代码里面显式调用GC
#-XX:MaxMetaspaceSize=256M 设置元空间为256M
#-XX:+PrintGCTimeStamps 输出GC的时间戳（以基准时间的形式）
#-XX:+PrintGCDateStamps 输出GC的时间戳（以日期的形式，如 2019-1-2T21:53:59.234+0800）
#-XX:+UseCMSCompactAtFullCollection 使用并发收集器时,开启对年老代的压缩UseCMSCompactAtFullCollection
#-verbose:gc 在输出设备上显示虚拟机运行信息

JAVA_OPTS="-Dspring.profiles.active=$EVN
  -Dserver.port=$PORT -Duser.timezone=GMT+8 -server
  -Djava.awt.headless=true
  -Xdebug -Xrunjdwp:transport=dt_socket,suspend=n,server=y,address=${DEBUG_PORT}
  -Xmx128m -Xms128m -Xmn128m -XX:PermSize=128m -Xss256k -XX:+DisableExplicitGC
  -XX:MaxMetaspaceSize=512M -verbose:gc
  -XX:MetaspaceSize=200m 
  -XX:+UseG1GC -XX:MaxGCPauseMillis=200
  -XX:InitiatingHeapOccupancyPercent=45
  -XX:NewRatio=2 -XX:SurvivorRatio=8
  -XX:MaxTenuringThreshold=15
  -XX:ParallelGCThreads=20
  -XX:ConcGCThreads=20
  -XX:G1HeapRegionSize=32m
  -XX:+UseFastAccessorMethods
  -XX:LargePageSizeInBytes=128m
  -XX:+PrintGC
  -XX:+UseGCLogFileRotation
  -XX:NumberOfGCLogFiles=10
  -XX:GCLogFileSize=20M
  -XX:+PrintGCDetails
  -XX:+PrintGCDateStamps
  -XX:+PrintGCTimeStamps
  -XX:+PrintHeapAtGC
  -XX:+TraceClassUnloading
  -XX:+PrintCompilation
  -XX:+CITime
  -Xloggc:${LOG_DIR}/gc-%t.log
  -XX:ErrorFile=${LOG_DIR}/java_error_%p.log
  -XX:HeapDumpPath=${LOG_DIR}/java_error.hprof"

for jarfile in "$Project_HOME"/lib/*.jar
do
   CLASSPATH="$CLASSPATH":"$jarfile"
done



#-------------------------------------------------------------------------------------------------------------
#getPID()-->拿到Java应用的PID
#说明:通过JDK自带的JPS命令及grep命令,精准查找Java应用的PID
#其中:[jps -l]表示显示Java主程序的完整包路径
#     awk命令可以分割出PID($1部分)及Java主程序名称($2部分)
#例子:[$jps -l | grep $APPLICATION_MAIN]-->>[5775 jrx.anytxn.cms.App]
#另外:用这个命令也可以直接取到程序的PID-->>[ps aux|grep java|grep $APPLICATION_MAIN|grep -v grep|awk '{print $2}']
#-------------------------------------------------------------------------------------------------------------
#初始化全局变量tradePortalPID,用于标识交易前置系统的PID,0表示未启动
TPID=0

getPID(){
    javaps=`jps -l | grep $APPLICATION_MAIN`
    if [ -n "$javaps" ]; then
        TPID=`echo $javaps | awk '{print $1}'`
    else
        TPID=0
    fi
}

logDir(){
    echo $LOG_DIR
    if [ ! -d "$LOG_DIR" ]; then
        mkdir "$LOG_DIR"
    fi
}

#清理系统缓存
clearSystemCache(){

echo ">>>>>>>>>>>>>>>>>>>>>>开始执行清除" $EVN "系统环境环境缓存<<<<<<<<<<<<<<<<<<<<<<<<<<<"

#drop_caches的值可以是0-3之间的数字，代表不同的含义：
#0：不释放（系统默认值）
#1：释放页缓存
#2：释放dentries和inodes
#3：释放所有缓存

#释放内存前先使用sync命令做同步，以保证文件系统的完整性，将所有未写的系统缓冲区写到磁盘中
#包含已修改的 i-node、已延迟的块 I/O 和读写映射文件。否则在释放缓存的过程中，可能会丢失未保存的文件。
echo ">>>>>>>>>>>>>>>>>>>>>>执行清理文件系统缓存和无用对象和它们占用的内存<<<<<<<<<<<<<<<<<<<<<<<<<<<"
sync

#清理pagecache（页面缓存）
echo ">>>>>>>>>>>>>>>>>>>>>>执行清理pagecache(页面缓存)<<<<<<<<<<<<<<<<<<<<<<<<<<<"
echo 1 > /proc/sys/vm/drop_caches

#清理dentries（目录缓存）和inodes
echo ">>>>>>>>>>>>>>>>>>>>>>执行清理dentries（目录缓存）和inodes<<<<<<<<<<<<<<<<<<<<<<<<<<<"
echo 2 > /proc/sys/vm/drop_caches

#清理pagecache、dentries和inodes
echo ">>>>>>>>>>>>>>>>>>>>>>执行清理pagecache、dentries和inodes<<<<<<<<<<<<<<<<<<<<<<<<<<<"
echo 3 > /proc/sys/vm/drop_caches

echo ">>>>>>>>>>>>>>>>>>>>>>释放完内存后让系统重新自动分配内存<<<<<<<<<<<<<<<<<<<<<<<<<<<"
echo 0 > /proc/sys/vm/drop_caches

}

startup(){
    getPID
    logDir
    #clearSystemCache
    echo "---------------------------------------------------------------------------------------------------------------------------"
    echo ">>>>>>>>>>>>>>>>>>>>>>>>>>>>JAVA_OPTS:" $JAVA_OPTS "<<<<<<<<<<<<<<<<<<<<<<"
    if [ $TPID -ne 0 ]; then
        echo "$APP_MAIN already started(PID=$TPID)"
        echo "---------------------------------------------------------------------------------------------------------------------------"
    else
        echo -n "Starting $APPLICATION_MAIN"
        nohup java $JAVA_OPTS -classpath $CLASSPATH $APPLICATION_MAIN >/dev/null 2>&1 &
        getPID
        if [ $TPID -ne 0 ]; then
            echo "(PID=$TPID)...[Success]"
            echo "---------------------------------------------------------------------------------------------------------------------------"
        else
            echo "[Failed]"
            echo "---------------------------------------------------------------------------------------------------------------------------"
        fi
    fi
}

startup

#tail -f $LOG_DIR/nohup.log

```

## Window安装MySQL5.7

### 1，下载解压包

```
https://downloads.mysql.com/archives/community/
```

### 2，解压到指定位置，如D盘

### 3，配置MySQL环境变量

- 新建环境变量MYSQL_HOME，值为解压的MySQL地址
- 配置PATH的环境变量： %MYSQL_HOME%\bin
- 在MySQL解压地址下配置my.ini

```tex
[mysqld]
#端口号
port = 3306
#mysql-5.7.37-winx64的路径
basedir="D:\MySQL\mysql-5.7.39-winx64"
#mysql-5.7.37-winx64的路径+\data
datadir="D:\MySQL\mysql-5.7.39-winx64\data"
#最大连接数
max_connections=200
#编码
character-set-server=utf8
default-storage-engine=INNODB
sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
[mysql]
#编码
default-character-set=utf8
```

​	**注意要在MySQL解压地址下建立data文件**

### 4，初始化MySQL

1，使用系统管理员身份运行CMD，首先执行以下命令:

此命令是安装MySQL服务

```shell
mysqld -install
```

2，执行以下命令

```shell
mysqld --initialize
```

3，启动MySQL服务

```shell
net start mysql
```

如果能启动成功，则说明安装成功

3，关闭MySQL服务

```shell
net stop mysql
```

###  5，修改MySQL密码

1，使用系统管理员身份运行CMD，首先执行以下命令:

此处是绕过MySQL的认证机制

```shell
mysqld --skip-grant-tables
```

2，重新打开一个CMD窗口，执行以下命令:

无密码登录MySQL

```shell
mysql -uroot -p
```

切换数据库

```shell
use mysql;
```

更新密码为123456

```shell
update user set authentication_string=password('123456') where user='root';
```

然后退出各个CMD窗口，再打开CMD窗口执行启动命令即可

```shell
net start mysql
```

## Window安装MySQL8.0

### 1，下载解压包

```
https://downloads.mysql.com/archives/community/
```

### 2，解压到指定位置，如D盘

### 3，配置MySQL环境变量

- 新建环境变量MYSQL_HOME，值为解压的MySQL地址
- 配置PATH的环境变量： %MYSQL_HOME%\bin
- 在MySQL解压地址下配置my.ini

```tex
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录 Docker部署则不需要
basedir=D:\MySQL\mysql-8.0.34-winx64
# 设置mysql数据库的数据的存放目录
datadir=D:\MySQL\mysql-8.0.34-winx64\data
# 允许最大连接数
max_connections=1000
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=100
# 服务端使用的字符集默认为UTF8
character-set-server=utf8mb4
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
#是否对sql语句大小写敏感，1表示不敏感
lower_case_table_names = 1
#MySQL连接闲置超过一定时间后(单位：秒)将会被强行关闭
#MySQL默认的wait_timeout  值为8个小时, interactive_timeout参数需要同时配置才能生效
interactive_timeout = 1800
wait_timeout = 1800
#Metadata Lock最大时长（秒）， 一般用于控制 alter操作的最大时长sine mysql5.6
#执行 DML操作时除了增加innodb事务锁外还增加Metadata Lock，其他alter（DDL）session将阻塞
lock_wait_timeout = 3600
#内部内存临时表的最大值。
#比如大数据量的group by ,order by时可能用到临时表，
#超过了这个值将写入磁盘，系统IO压力增大
tmp_table_size = 64M
max_heap_table_size = 64M
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8mb4
[client]
# 设置mysql客户端连接服务端时默认使用的端口
port=3306
default-character-set=utf8mb4
```

   **注意要在MySQL解压地址下建立data文件**

### 4，初始化MySQL

1，初始化MySQL

```shell
mysqld --initialize --console
```

2，安装MySQL

```shell
mysqld --install mysql
```

3，启动MySQL服务

```shell
net start mysql
```

如果能启动成功，则说明安装成功

3，关闭MySQL服务

```shell
net stop mysql
```

###  5，修改MySQL密码

1，使用系统管理员身份运行CMD，首先执行以下命令:

此处是绕过MySQL的认证机制

```shell
mysqld --console --skip-grant-tables --shared-memory
```

2，重新打开一个CMD窗口，执行以下命令:

无密码登录MySQL

```shell
mysql -uroot -p
```

切换数据库

```shell
use mysql;
```

先刷新权限，才可以更新密码

```shell
flush privileges;
```

更新密码为123456 (初始化的时候只有root账户在localhost下链接)

```shell
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
```

再次刷新权限

```shell
flush privileges;
```

然后退出各个CMD窗口，再打开CMD窗口执行启动命令即可

```shell
net start mysql
```

### Windows卸载MySQL5.5、5.7

1，直接在控制面板卸载MySQL程序。

2，在Windows注册表中删除如下文件夹的内容。

**HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL\ 文件夹。
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\Eventlog\Application\MySQL\ 文件夹。
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application\MySQL\ 文件夹。**

## 安装需要设置的环境变量

**JAVA_HOME**

```shell
D:\Java\jdk8u362-b09
```

**NODE_HOME**

```shell
D:\NodeJS
```

**MAVEN_HOME**

```shell
D:\Maven\apache-maven-3.8.4
```

**MYSQL_HOME**

```shell
D:\MySQL\mysql-8.0.27-winx64
```

**PATH环境变量设置**

%MYSQL_HOME%\bin
%JAVA_HOME%\bin
%MAVEN_HOME%\bin

%NODE_HOME%\Node
%NODE_HOME%\node_global

### VsCode的settings文件配置

```json
{
  "workbench.colorTheme": "Solarized Light",
  "editor.fontSize": 16,
  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": false,
  "solidity.telemetry": true,
  "editor.codeActionsOnSave": {
  
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "editor.formatOnSave": true,
  "settingsSync.ignoredExtensions": [],
  "workbench.colorCustomizations": {
    //设置用户选中代码段的颜色
    "editor.selectionBackground": "#7c9fe0",
    "editor.selectionHighlightBackground": "#7c9fe0",
    //设置活动tab窗口颜色
    "tab.activeBackground": "#5f80629a"
  },
  "settingsSync.ignoredSettings": [],
  //可以格式化Solidity
  "[solidity]": {
    "editor.defaultFormatter": "NomicFoundation.hardhat-solidity"
  },
  "editor.fontLigatures": false,
  "terminal.integrated.fontSize": 16,
  "notebook.editorOptionsCustomizations": {},
  "editor.fontVariations": false,
  "git.openRepositoryInParentFolders": "never"
}

```





#### 未完待续 。。。
