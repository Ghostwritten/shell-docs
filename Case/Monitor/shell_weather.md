#  Shell 天气预报
tags: 监控

 - `weather.sh`

```bash
#!/bin/bash
# weather.sh
# Copyright 2018 computer-geek64. All rights reserved.

program=Weather
version=1.1
year=2018
developer=computer-geek64

case $1 in
-h | --help)
	echo "$program $version"
	echo "Copyright $year $developer. All rights reserved."
	echo
	echo "Usage: weather [options]"
	echo "Option          Long Option             Description"
	echo "-h              --help                  Show the help screen"
	echo "-l [location]   --location [location]   Specifies the location"
	;;
-l | --location)
	curl https://wttr.in/$2
	;;
*)
	curl https://wttr.in
	;;
esac
```

执行：
```bash
$ bash weather.sh -h
Weather 1.1
Copyright 2018 computer-geek64. All rights reserved.

Usage: weather [options]
Option          Long Option             Description
-h              --help                  Show the help screen
-l [location]   --location [location]   Specifies the location


$ bash weather.sh 
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ca42d896d6d2406aac57c7dd65d7d8ff.png)

```bash
$ bash weather.sh -l shanghai
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/9b34d16d6da84a6a99879a4cd1c40192.png)
