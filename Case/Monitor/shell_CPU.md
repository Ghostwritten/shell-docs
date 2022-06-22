#  shell CPU
tags: 监控

## 1.  shell CPU 使用率
- `CPU.sh`
```bash
MAX=95
EMAIL=server@127.0.0.1

USE=$(grep 'cpu ' /proc/stat | awk '{usage=($2+$4)*100/($2+$4+$5)} END {print usage ""}')
USE=`printf "%.0f\n" $USE`
if [[ $USE -gt $MAX ]]; then
   echo "Percent used: $USE" | mail -s "Running out of CPU power" $EMAIL
else
   echo "all is well !"
fi
```
执行：

```bash
$ bash CPU.sh
all is well !
```
更多阅读：

 - [CPU使用率达到100%怎么办？](https://blog.csdn.net/xixihahalelehehe/article/details/117926926)
 - [系统中的软中断使用率升高怎么办？](https://blog.csdn.net/xixihahalelehehe/article/details/117991825)
 - [如何快速分析出CPU的瓶颈？](https://blog.csdn.net/xixihahalelehehe/article/details/118178337)
 - [CPU使用率高却找不到应用？](https://blog.csdn.net/xixihahalelehehe/article/details/117961015)
