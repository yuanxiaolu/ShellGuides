# ShellGuides

#### 1. Compare paramter 参数的比较 [Bash warning - argument expected](https://stackoverflow.com/questions/29178135/bash-warning-argument-expected)
```
if [ ${OUTPUT} = "" ]
                   ^--- Required
if [ "${OUTPUT}" = "" ]
     ^-- Here -^
```     
#### shell脚本中用awk避免unexpected newline or end of string报错
```
xxx.sh
ssh root@${ip} 'helm list --col-width 200 | sed 1d | awk '{print $9}' | sort | uniq'

改成
line='$9'
ssh root@${ip} "helm list --col-width 200 | sed 1d | awk '{print $line}' | sort | uniq"
```

#### shell脚本中要远程登录目标机器并执行命令
```s
if [ -z "$1" ];
then
ip="";
else
ip=$1;
fi

ssh root@${ip} 'kubectl logs -f -n nebula podname --tail 0' > ./${filename}.txt

```
#### Multiple threads in shell script比如发送请求同时记录日志
```s
read_cfg cfgA &
read_cfg cfgB &
read_cfg cfgC &
wait

all those jobs will then run in the background simultaneously. The optional wait command will then wait for all the jobs to finish.
```
#### while循环总是为true的写法
```s
Colon is always "true":
while :; do foo; sleep 2; done
```
