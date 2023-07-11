# OCEANBASE-OCEANBASE同步链路
## 源端部署

>1.解压安装同上ob做源端部分

[请点此跳转查看](README.md)

>2.登录web客户端进行安装

<details>
<summary>fzs-source</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/1.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/2.png)

<font color="red">提示：选择同步模式</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/3.png)

<font color="red">提示：勾选需要同步的对象</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/4.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/5.png)

<font color="red">提示：按照实际情况修改全同步并发数</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/6.png)

<pre>
<font color="red">提示：</font></br>
1.输入目标端IP和端口，端口可以默认不做修改 </br>
2.web端口是网页与软件之间通信端口</br>
3.数据端口是软件源端与目标端通信端口</br>
</pre>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/7.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/8.png)

<pre>
<font color="red">提示：</font></br>
1.可更换通信端口也可以使用默认端口</br>
2.此页面端口为源端进程内部通信端口</br>
</pre>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/9.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/10.png)

>3.配置Oceanbase配置信息

<pre>
配置 liboblog.conf 文件
cluster_user=** // 说明：sys 租户下创建的 user，具有内部表的读权限
cluster_password=**  // 说明，上述用户密码
cluster_url=**  // 说明： 集群 obconfig url，OB 集群的标示,获取方法：show parameters like '%obconfig_url%';
tb_white_list=*.*.* //说明：设置拉取的白名单，格式为 租户名.库名.表名
enable_output_hidden_primary_key=1 //说明： 输出隐藏主键列
</pre>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/11.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/12.png)

<font size="6"><span style="font-weight: bold">源端配置完成!</span></font>
</details>
<hr style="border: 2px solid grey;">

## 备端部署

>1.解压配置同上ob做备端的配置

>2.登录web客户端，进行安装

<details>
<summary>fzs-tgt</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/1.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/2.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/3.png)

<font color="red">提示：</br>1.上面目标端内部通信端口参数可以修改也可以保持默认</br>2.最下面配置源端IP地址及web端口</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/4.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/5.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/6.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/ob-ob/ob--ob-tgt/7.png)

<font size="6"><span style="font-weight: bold">ob--ob配置完成!</span></font>
</details>
<hr style="border: 2px solid grey;">
