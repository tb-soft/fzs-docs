# OCEANBASE--ORACLE同步链路
## 部署注意事项
>注意事项

1. OB端 需要执行一下其中一个操作：
<pre>
create user '__OCEANBASE_INNER_DRC_USER'@'%' identified by synjq; </br>
grant ALL to '__OCEANBASE_INNER_DRC_USER';
</pre>

2. 提前创建好 __OCEANBASE_INNER_DRC_USER 用户，并提供相应密码

## 源端部署


>1.上传软件包并解压到指定目录，并将授权文件sn.txt放到conf目录下

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-sn.png)

>2.根据实际情况修改conf/web.conf文件的web端口，及web_login参数

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-webconf-login.png)

>3.进入run目录启动web端口

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-fzsweb.png)

>4.使用web客户端进行安装

<pre>
1.使用浏览器登录到九桥同步软件界面
2.ip为源端机器ip地址，端口默认为8303,如有需要可以修改
3.用户名密码为admin/admin
<font color="red">注：建议不要使用IE浏览器，可能会出现乱码</font>>
</pre>
<details>
<summary>源端-web详细配置步骤</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web.png)

>5.系统安装

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web1.png)


>6.按照提示点击下一步


![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web2.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web3.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web4.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web5.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web6.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web7.png)

>7.选择同步模式--下一步

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web8.png)

>8.勾选要同步的对象--下一步

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web9.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web10.png)

>9.按照实际情况修改全同步并发数--下一步

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web11.png)

<pre>
<font color="red">
1.输入目标端IP和端口，端口可以默认不做修改
2.web端口是网页与软件之间通信端口
3.数据端口是软件源端与目标端通信端口</font>
</pre>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web12.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web13.png)

<pre>
<font color="red">
1.可更换通信端口也可以使用默认端口
2.此页面端口为源端进程内部通信端口
3.export内存限制改为40960，否则会出现进程内存溢出重启
</font>
</pre>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web14.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web15.png)

>10.填写OceanBase配置信息

<pre>
配置 liboblog.conf 文件
cluster_user=** // 说明：sys 租户下创建的 user，具有内部表的读权限
cluster_password=**  // 说明，上述用户密码
cluster_url=**  // 说明： 集群 obconfig url，OB 集群的标示,获取方法：show parameters like '%obconfig_url%';
tb_white_list=*.*.* //说明：设置拉取的白名单，格式为 租户名.库名.表名
enable_output_hidden_primary_key=1 //说明： 输出隐藏主键列
</pre>
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web16.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web17.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web18.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-web19.png)



<font size="6"><span style="font-weight: bold">源端配置完成!</span></font>
</details>
<hr style="border: 2px solid grey;">

## 目标端部署

<pre>
前面安装同源端安装一样，按照提示执行下一步即可
</pre>

<details>
<summary>fzs-tgt</summary>

![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-1.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-2.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-3.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-4.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-5.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-6.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-7.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-8.png)
![](https://image-1302181629.cos.ap-beijing.myqcloud.com/fzs-images/fzs-tgt-image/fzs-tgt-9.png)

</details>

<hr style="border: 2px solid grey;">

<font size='5'>ob--oracle部署完毕</font>

[<p align="right"> <font size='5'>下一页</font></p>](oracle--ob链路.md)