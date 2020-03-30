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
