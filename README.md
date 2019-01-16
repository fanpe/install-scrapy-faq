# install scrapy's question
## 安装scrapy时遇到的坑，并对问题整理方便自己及别人参考
**本机为MAC系统，除了默认带有python2.7外，还安装了python3.7版本，已经安装了PIP（如果在终端pip install xxx时，系统默认是安装在3.7版本)**
## 根据本机情况：
   * 终端安装：pip install scrapy,出现了**带红字**提示说：没有安装依赖库Twisted('Failed building wheel for Twisted')
   * 那就只能安装提示的依赖库：`pip install twisted`,结果提示：xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun
   * 因此我下载了.WEL安装还是不行，最后网上说是
     > MAC系统更新啥的
     > 使用命令：`sudo xcode-select --install`安装了什么东西，我也不懂
   * 然后再安装twisted就成功了。附上文章：(https://www.cnblogs.com/espooky/p/5979920.html)
   * 再来安装：`pip install scrapy`,成功了:sob:
   * CD进入项目目录，然后终端执行：`scrapy startproject test`创建TEST项目，结果提示说文件没找到或已损坏
   * > 网上大神说是scrapy安装的默认路径要在/usr/bin里面，然而我没有找到，却在/usr/local/bin找到了
   * 那么就终端输入命令：`sudo cp /usr/local/bin/scrapy /usr/bin/scrapy`来复制，提示无权限
   * 重启系统长按：command+r进入保护模式，打开窗口上方的菜单，找到终端输入：csrutil disable
   * 再次执行：`sudo cp /usr/local/bin/scrapy /usr/bin/scrapy`命令，成功了，再创建项目：`scrapy startproject test`，终于成功啦
### 以下内容可以忽略
   ~~总结一下：刚接触mac osx系统真心不友好，有很多限制，但安全系数高及系统文件管理很赞，上手比WINDOWS难，但熟悉命令后，比WIN快，很酷的感觉有木有
           完成后记得：csrutil enable~~
