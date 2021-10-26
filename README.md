# WeNet-router
## 项目更改，毕业啦公开啦。
#### 本项目是对wenet及其类似软件或采用portal协议的网络认证，使用路由器一号共享网络。
锐捷全版本适用请移步[F-Light-intercept-singlenetpppoe](https://github.com/F-Light/intercept-singlenetpppoe)    
---------------------------------------------------------------- 
*实现功能:  
①电脑端和手机端登入切换，两种共享方式，电脑端原理参考
[issue #138](https://github.com/miao1007/Openwrt-NetKeeper/issues/138)，
同时也copy了[huipengly/Openwrt-NetKeeper](https://github.com/huipengly/Openwrt-NetKeeper/tree/master/netkeeper4-use-pppoer-server) 代码.  
②手机端wenet登入后，路由器共享网络。 
- -------------------------------------------------------------------------------  

该脚本目前仅在 mtk 7260，PandoraBox固件测试通过，其余平台请自行研究，测试平台①newifi mini，5G wifi关闭。测试平台②斐讯k2，测试平台③某云工模mtk7260  
- 打开5g wifi需要修改/etc/dialtool，
        uci set wireless.@wifi-iface[x]，x与wifi数量相关。
- 其他平台（固件：openwrt，lede）需要修改/etc/dialtool，
        iwinfo **ra1** assoclist | head -n 1 | awk '{print $1}'，主要是无线网卡的名称问题，请自行修改
  
- **辽宁地区测试可用**，外地只要是用wenet，或是类似portal认证的，**理论可用**。  
- 原理为:用户手机went向portal服务器发送MAC地址及其时间戳认证密匙，并通过认证。
- 此时该MAC地址被服务器绑定pass标签，使用此MAC地址的设备并保持数据连接可获得pass。
- ~~暂时不提供使用教程~~。
- **业余爱好，能力有限**，自用为主。需要者，需了解openwrt的一些操作，修改/etc/dialtool 文件。
- 本人还用E4A 做了配套的app，方便快速拨号。（未修改，验证码绝对出错，如果需求的人多，我可以重新编译或者放出e4a源文件）  
- 偷懒者，请在一个干净的**PandoraBox固件恢复上传 WeNet-router.tar.gz**。 
- -------------------------------------------------------------------------------  
**文件说明：**  
/etc/dialtool 主要脚本  
~~/etc/int.d/   本人用于校园网路由器禁用ssh和telnet，超低级限制   ！！请自行删除！！~~  
~~/etc/shadow   openwrt账户密码文件----  ！！请自行删除！！~~  
/root/        一些小小的安装包  
/www/cgi-bin 用于网页页面以及app的一些辅助脚本
          
