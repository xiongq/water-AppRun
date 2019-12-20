# water-AppRun
## 小窗口水印  
##### version: v2.12
##### code: qt
##### author: xiongq

#### 1.linux 打包发布
> 教程来源于 https://blog.csdn.net/u014746574/article/details/79288727

#### 2.有可能依赖不完整

> 虽然linuxdepoyqt可以帮我们解决多数情况下库的依赖问题，但是也有的时候不能完整解决。这个时候就需要我们自己复制所依赖的库。
提供一个脚本，复制依赖库，复制以下代码，将其保存成为 copylib.sh

> #!/bin/sh
> bin=$1         #发布的程序名称  
> desDir="./lib" #你的路径  
> if [ ! -d $desDir ];then
>       #echo "makedir $desDir"
>       mkdir $desDir
> fi 
> libList=$(ldd $bin | awk  '{if (match($3,"/")){ printf("%s "),$3 } }')
> cp $libList $desDir

#### 关键步骤
> linuxdeployqt ./myQtApp -appimage
