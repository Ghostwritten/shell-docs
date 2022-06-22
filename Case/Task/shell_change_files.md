#  shell 批量修改文件名
tags: 任务

@[toc]

---
## 1. 添加

```bash
$ ls
file1  file2  file3  file4
$ cat mv1.sh
#!/bin/bash
for file in `ls file*`
do
   mv $file `echo "${file}.txt" `
done

$ bash mv1.sh 
$ ls
file1.txt  file2.txt  file3.txt  file4.txt
```
```bash
$ ls
file.1  file.2  file.3  file.4
$ cat mv1.sh
#!/bin/bash
for file in `ls file*`
do 
   #mv $file  `echo ${file}.txt|sed 's/\.//1' `
   mv $file $(echo ${file}.txt|sed 's/\.//1')
done


$ bash mv1.sh 
$ ls
file1.txt  file2.txt  file3.txt  file4.txt
```
## 2. 修改

```bash
$ ls
file1.txt  file2.txt  file3.txt  file4.txt 

$ cat mv3.sh
#!/bin/bash
for file in `ls file*`
do
   mv $file ${file%.txt}.sh    #第一种方法
done

$ bash mv3.sh 
$ ls
file1.sh  file2.sh  file3.sh  file4.sh

$ cat mv4.sh
#!/bin/bash
for file in `ls file*`
do
   mv $file `echo $file |sed 's/\.sh/\.pdf/'`   #第二种方法
done

$ bash mv4.sh
$  ls
file1.pdf  file3.pdf  file2.pdf  file4.pdf 

```
## 3. 删除

```bash
$  ls
file1.pdf  file3.pdf  file2.pdf  file4.pdf 

$ cat mv5.sh
#!/bin/bash
for file in `ls file*`
do
   mv $file `echo $file |sed 's/\.pdf//'`
done

bash mv5.sh
$ ls
file1  file2  file3  file4
```

