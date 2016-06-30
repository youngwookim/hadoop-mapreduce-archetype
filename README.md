hadoop-mapreduce-archetype
==========================

An archetype for creating a basic, self-contained Hadoop MapReduce job.

## Prerequisites
Maven 3.x


## Build and Install maven archetype
```
$ git clone https://github.com/youngwookim/hadoop-mapreduce-archetype.git
$ cd hadoop-mapreduce-archetype
$ mvn clean install

```

## Create a MapReduce project
```
$ mvn archetype:generate -Dfilter=com.xyz:hadoop-mapreduce-archetype
...
1: local -> com.xyz:hadoop-mapreduce-archetype (An archetype for creating a basic, self-contained Hadoop MapReduce job.)
Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): : 1
Define value for property 'groupId': : com.ywkim
Define value for property 'artifactId': : WordCount
Define value for property 'version':  1.0-SNAPSHOT: : 
Define value for property 'package':  com.ywkim: : 
Confirm properties configuration:
groupId: com.ywkim
artifactId: WordCount
version: 1.0-SNAPSHOT
package: com.ywkim
 Y: : Y

...
```

## 프로젝트 빌드하기
```
$ cd WordCount
$ mvn eclipse:eclipse -DdownloadSources=true -DdownloadJavadocs=true
$ mvn clean package

```

## 애플리케이션 배포하고 실행하기
데이터 준비하기:
```
# hadoop fs -put /etc/DIR_COLORS /user/root/

```

MapReduce 애플리케이션 실행하기: 
```
# yarn jar WordCount-1.0-SNAPSHOT-mr-job.jar -Dmapreduce.job.queuename=root.default /user/root/DIR_COLORS /user/root/result

...
```

결과 확인:
```
# hadoop fs -ls /user/root/result/
Found 3 items
-rw-r--r--   1 root root          0 2014-02-10 14:17 /user/root/result/_SUCCESS
drwxr-xr-x   - root root          0 2014-02-10 14:16 /user/root/result/_logs
-rw-r--r--   1 root root       3639 2014-02-10 14:17 /user/root/result/part-r-00000

# hadoop fs -cat /user/root/result/part-*
```

```
"normal"	1
#	52
#.bat	1

......

you	3
your	1

```


