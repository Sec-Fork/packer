## 1.说明

packer.exe -f beacon.bin -l ZhiZhen

默认 ZhiZhen 加载运行可以过wdf和火绒(默认是隐藏黑窗口的,http/https协议都可以)
一直可以(这马子保真),createThread 加载也可以
编译方式为(通过代码隐藏黑窗口):
go build -ldflags="-w" main.go


注意: 如果编译失败很有可能是模板文件中的依赖没有下载

批量编译
packer.exe -f beacon.bin -l all

vps测试,发现 syscall 不加任何编译参数,可以绕过360,360安全大脑
目前对此程序的判断是可以程序,非木马,通过添加qq资源文件,可以直接
绕过可以,上线cs,上线之后,立即迁移了进程,删除了样本文件

笔记: createfiber 和 ntqueueapcthreadex 360查杀
综合体验 针对360 bypass syscall免杀好一点

github.com/gonutz/ide/w32
golang.org/x/sys/windows  需要打包进依赖

必须 配置go环境

针对bypass360, go的编译,不加参数,或者只加一个-w比较好用

cs的profile文件(windows 更新的流量),该配还是要配的

win10虚拟机测试
jsq测试
sysenumsourcefiles  虚拟机/物理机失败
createfiber 虚拟机/物理机失败
ntqueueapcthreadex  虚拟机/物理机失败

使用者必须有go环境

在虚拟机使用1.18的go编译,清楚go信息加入成功

下一步,进行goland+git+github仓库发布项目(实现)

火绒,查杀syscall直接调用,石锤(实现)

样本火绒报毒之后,360立马也从免杀到报毒,你大爷的(验证)

测试:(不添加任何编译参数,使用payload.c)
CertEnumSystemStore.txt  bypass360 不支持sgn加密shellcode
CertEnumSystemStoreLocation.txt 疑似shellcode长度限制,导致无法上线,计算器是ok
createfiber.txt  bypass360 不支持sgn加密shellcode
createprocesswithpipe.txt
createremotethread.txt   360查杀
createremotethreadex.txt  360查杀
createthread.txt 360查杀
createthreadnative.txt 360查杀
CreateThreadPoolWait.txt 360查杀
CreateTimerQueueTimer_Tech.txt  360查杀
creatprocess.txt  360查杀
CryptEnumOIDInfo.txt
earlybird.txt
enumthreadwindows.txt
enumwindows.txt   不上线就奇怪
etwpcreateetwthread.txt
heapalloc.txt   bypass360
ntqueueapcthreadex.txt
proccryptprotectmemory.txt
rtlmovememory.txt   bypass360
syscall.txt
syscall1.txt
sysenumsourcefiles.txt
uuidfromstring.txt   bypass360
zhizhen.txt

不采用sgn进行shellcode加密

加密,解密的代码全部封装到结构体中