# 抖音协议点赞、评论、直播弹幕加密算法研究分析

首先这里有一篇关于Android逆向工程的文章，反编译了抖音的libuserinfo.so文件的种种加密入口限制，使得自己的Android程序可以调用该so文件直接加密校验。这样的效果就是无需真正意义破解加密算法。<br />这里直接讲抖音的加密算法本身。火山小视频也一样。我们拿来进行研究分析学习下。仅供学习交流。<br />**抖音核心协议的步骤是**：<br />　　1、在查询串插入一个固定的键rstr<br />　　2、对查询串进行按键排序并取值，对空格和+进行转义为a<br />　　3、然后取MD5；如果时间轴&1为1，那么取多一次MD5<br />　　4、将MD5结果分别和5******6、1******4进行2次错位排序算法<br />　　5、将4的结果再进行一次错位排序，得到26位字符<br />　　6、将字符分别取18位给到as和cp字段，追加到查询串最后<br />
<br />　　在最新的SDK版本有了新的mas字段辅助校验，这个完全可以忽略，只要把查询串的version_code设置到169之前就可以跳过这个字段了。<br />
<br />　　另外aid为必填字段，其他和接口本身无关的字段都可去掉。<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/97322/1606869601754-d7813825-edfd-4c50-8c9e-8d2ebd36dcd5.png#align=left&display=inline&height=518&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1036&originWidth=1240&size=645693&status=done&style=none&width=620)<br />抖音协议、火山小视频通信协议<br /> <br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/97322/1606869619423-1af4d2fe-7034-417e-a669-242e184982a6.png#align=left&display=inline&height=513&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1026&originWidth=1238&size=515131&status=done&style=none&width=619)<br />抖音协议、火山小视频通信协议<br /> <br />由于这里涉及到抖音公司的核心利益，就不放具体代码和关键Key值了。仅供研究加密算法学习。<br />
<br />——————————————————————————————————————————————
<a name="9794cc28"></a>
#### TiToData：专业的短视频、直播数据接口服务平台。
<a name="1c5f89ff"></a>
#### 更多信息请联系： [TiToData](https://www.titodata.com?from=douyinarticle)
覆盖主流平台：抖音，快手，小红书，TikTok，YouTube
