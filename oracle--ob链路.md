# Oracle-OceanBase同步链路
## 源端部署
> 1.上传软件包并解压到指定目录，执行setup_linux64_11g.sh脚本，并将授权文件sn.txt放到conf目录下

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/1.png)

>2.根据实际情况修改conf/web.conf文件的web端口，进入run目录启动源端web端口

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/2.png)

>3.使用web客户端进行安装

<pre>
1.使用浏览器登录到九桥同步软件界面
2.ip为源端机器ip地址，端口默认为8303,如有需要可以修改
3.用户名密码为admin/admin
<font color="red">注：建议不要使用IE浏览器，可能会出现乱码</font>
</pre>
<details>
<summary>fzs-source</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/3.png)

>4.点击系统安装按照提示进行下一步操作

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/4.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/5.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/6.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/7.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/8.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/9.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/10.png)

>5.到此选择需要同步的模式

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/11.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/12.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/13.png)

<font color="red">提示：根据实际情况修改全量并发数</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/14.png)

>6.下一步配置目标端的ip等相关信息

<pre>
1.输入目标端IP和端口，端口可以默认不做修改
2.web端口是网页与软件之间通信端口
3.数据端口是软件源端与目标端通信端口
</pre>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/15.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/16.png)

<font color="red">提示：</br>可更换通信端口也可以使用默认端口</br>此页面端口为源端进程内部通信端口</font>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/17.png)
<font color="red">提示：当以ob数据库为备端时，勾选抽取数据时做文本转换+oceanbase目标端</font>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/18.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/19.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/20.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/21.png)

<font size="6"><span style="font-weight: bold">源端配置完成!</span></font>
</details>
<hr style="border: 2px solid grey;">

## 备端部署

>1.上传软件包并解压到指定目录，并将授权文件sn.txt放到conf目录下

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/1.png)

>2.根据实际情况修改conf/webt.conf文件的web端口，及web_login参数

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/2.png)

>3.进入run目录启动web端口

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/3.png)

>4.使用web登录客户端进行安装

<details>
<summary>fzs-tgt</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/4.png)

>5.点击系统安装按照提示信息下一步操作

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/5.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/6.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/7.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/8.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/9.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/10.png)

<font color="red">提示：alloc进程内存修改为2048</font>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/11.png)

<font color="red">提示：</br>上面目标端内部通信端口参数可以修改也可以保持默认</br>  最下面配置源端IP地址及web端口
</font>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/12.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/13.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/14.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/15.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/16.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/oracle--ob/oracle--ob-tgt/17.png)




<font size="6"><span style="font-weight: bold">备端配置完成!</span></font>
</details>
<hr style="border: 2px solid grey;">

[<p align="right"> <font size='5'>下一页</font></p>](ob-ob链路.md)


