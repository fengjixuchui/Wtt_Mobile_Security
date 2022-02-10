【安卓逆向小知识】 一行adb命令获取当前 APP窗口名 包名

```shell
adb shell dumpsys window | grep mCurrentFocus
```

ubuntu上  直接梭哈命令就可以了

![ubuntu dumpsys window 获取窗口](https://gitee.com/wangtietou/net_pic/raw/master/essay/ollvm/2/image-20210707191823626.png)

windows上如果直接运行  这行命令，就会

喜提报错。。。

![windows dumpsys window 获取窗口 报错](https://gitee.com/wangtietou/net_pic/raw/master/essay/wp/0707/image-20210707193114211.png)

这里报错的原因是因为，windows上并没有  grep这个过滤字符串的工具

那应该咋办？  

windows上过滤字符串 不用grep 用 findstr

所以命令就应该是：

```shell
adb shell dumpsys window | findstr mCurrentFocus
```

![windows dumpsys window 获取窗口](https://gitee.com/wangtietou/net_pic/raw/master/essay/wp/0707/image-20210707201353200.png)

**命令原理:**

dumpsys 是一个android系统上的，对服务进行调试诊断的工具。

下面是谷歌官方文档

![dumpsys 谷歌官方文档](https://gitee.com/wangtietou/net_pic/raw/master/essay/wp/0707/image-20210707195903135.png)

---

dumpsys window 会输出一大波 窗口相关的信息

![dumpsys window 相关信息](https://gitee.com/wangtietou/net_pic/raw/master/essay/wp/0707/image-20210707200040349.png)

那我们需要过滤自己想要的信息。

mCurrentFocus 拆开来是  m Current  Focus 

```
m		: 代码中对成员变量 member的缩写  
Current : 现在 当前
Focus   : 聚焦
```

所以 mCurrentFocus这个词，除了m没啥实际意义 纯粹就是编码规范加了个m

CurrentFocus 的意思就是 当前的焦点

![mCurrentFocus 获取窗口信息](https://gitee.com/wangtietou/net_pic/raw/master/essay/wp/0707/image-20210707200449471.png)

在dumpsys一大堆的输出信息中， mCurrentFocus 这一行会输出当前获得焦点的窗口

所以我们过滤一下就可了

```shell
//linux执行这行
adb shell dumpsys window | grep mCurrentFocus     

//windows执行这行
adb shell dumpsys window | findstr mCurrentFocus  
```



---

刚刚 盒马会员日，我为了蹭优惠买了点水果

看到女同事在加班，我就拿了个水果给她吃

女同事问我，是专门给她买的吗？

我说：不是，我就为了蹭下盒马会员日的优惠。

---

0707 王某某于 公司办公楼

