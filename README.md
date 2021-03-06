学历代表你的过去，能力代表你的现在，学习代表你的将来！

阿里图标https://www.iconfont.cn
ThinkPHP http://www.thinkphp.cn/down.html

CSS3响应式模板：[https://templated.co/](https://templated.co/)

[Android Studio](http://www.android-studio.org/)
### 阿里云ECS实例中 生产环境启动
一、启动redis, 打开控制台或终端 （或用阿里云远程连接）
```
# ssh root@39.108.xxx.xx
root@39.108.xxx.xx's password: 
# redis-server
```
二、打开控制台或终端 
1、确定redis是否启动
```
#redis-cli
127.0.0.1:6379> exit
```
2、启动nginx
```
# /usr/local/nginx/sbin/nginx 
```
3、删除系统日志
```
# cd /data/logs/nodes/
# ls -l
# rm -rf *.*
```
4、启动Web服务器
```
# cd /www/web/koa-redis-waiter/
# pm2 stop all
# pm2 start process.json
```

### CentOS 7启动nginx
```
whereis nginx
nginx: /usr/local/nginx
-bash-4.2# cd /usr/local/nginx/
sbin/nginx
```

### Mac 启动MongoDB
```
brew services restart mongodb@3.6
```
### CentOS/Mac 命令行远程连服务器
```
ssh root@39.108.XXX.42
root@39.108.XXX.42's password: 
```


# 0、JavaScript Stack
 - [1、MXXN Stack](../../tree/01-MXXN-Stack) 
 - [2、MEAN Stack](../../tree/02-MEAN-Stack)
 - [3、MERN Stack](../../tree/03-MERN-Stack)
 - [4、MKAN Stack](../../tree/04-MKAN-Stack) 
 - [5、MKRN Stack](../../tree/05-MKAN-Stack) 
 - [6、MKVN Stack](../../tree/06-MKAN-Stack) 
 - [7、RMXXN Stack](../../tree/07-RMXXN-Stack) 
 - [8、JavaScript实例](../../tree/08-JS-Action) 

# 1、MongoDB
- [1、MongoDB简介](../../tree/11-mongodb-introduction)
- [2、MongoDB安装](../../tree/11-mongodb-install)
- [3、MongoDB数据模型](../../tree/11-mongodb-data-model)
- [4、MongoDB查询数据](../../tree/11-mongodb-query-data)
- [5、MongoDB更新数据](../../tree/11-mongodb-Update-data)
- [6、MongoDB删除数据](../../tree/11-mongodb-delete-data])
- [7、MongoDB数据库管理](../../tree/11-mongodb-Database-management)
- [8､ MongoDB数据库备份还原](../../tree/11-mongodb-Database-backup-restore)
- [9、MongoDB 使用地理空间索引](../../tree/11-MongoDB-uses-geospatial-ndex)

# 2、Redis
- [Redis 的应用场景](../../tree/01-redis-application-cenarios)
- [Mastering Redis](https://github.com/PacktPublishing/Mastering-Redis)

# 3、Distributed Version Control System Git
- [1、Git 服务器搭建及存储库的创建](../../tree/31-Git-install)

# 4､ RMKVN & RMKRN & RMKAN

# 5､ 网站应用微信登录开发指南

# 6、RESTful API
- [创建API](../../tree/01-RESTful-API)
- [命令行测试API](../../tree/02-RESTful-API)

# 7、CentOS 7
- [1、命令](../../tree/01-centos7)
- [2、Nginx安装](../../tree/02-centos7-nginx)
- [3、Node.js安装](../../tree/03-centos7-nodejs)
- [4、Redis安装](../../tree/04-centos7-redis)
- [5、MongoDB安装](../../tree/05-centos7-mongodb)
- [6、RatHabitMQ安装](../../tree/06-centos7-rathabitmq)

# 8､ 实战实用技巧
- [1、Node.js Request发短信](../../tree/01-node-request-send-sms)
- [2、js实战实用技巧 (1)](../../tree/01-node-js-example-1)


# 9､ Vagrant
- [1、Vagrant](../../tree/01-vagrant-install)

# 10､ Lua & Cocos
https://docs.cocos.com/creator/manual/zh/getting-started/install.html
- [1、Lua](../../tree/01-Lua)
- [go web开发](https://github.com/astaxie/build-web-application-with-golang/blob/master/zh/preface.md)
- [egg-sequelize](https://github.com/eggjs/egg-sequelize)
- [Ramda](http://ramda.cn/docs/)

1，关于ace admin
https://blog.csdn.net/freewebsys/article/details/68955060
ace admin 是一个非常好的后台系统ui。 

集成了很多的好东西。非常的方便开发后天系统，而且能很漂亮。 

上面有一堆的例子。非常的漂亮。 

[http://ace.jeka.by/](http://ace.jeka.by/ )

前端样式参考[https://acekarts.com.au/]（https://acekarts.com.au/）



# 11､ 微信相关开发
## 1、网站应用微信登录开发指南
https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&id=open1419316505&token=&lang=zh_CN

## 2、微信JS-SDK说明文档
https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1455784140

## 3、微信 JS 接口签名校验工具
https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=jsapisign


'''
const xcxConst = require('../config/common/xcx.config')

const request = require('request')

const BaseHandler = require('../libs/baseHandler')
let controllers = new BaseHandler()

/* 微信登陆 */
const AppID  = xcxConst.APPID
const SECRET = xcxConst.AppSecret
const URI    = xcxConst.WEB_URL

controllers.wx_login = async (ctx, next)=>{
   
    const STATE        = uuidv4().split('-').join('')
    // 第一步：用户同意授权，获取code
    const CALLBACK     = 'get_wx_access_token';
    const REDIRECT_URI = `${encodeURIComponent(URI)}${CALLBACK}`  
    const SCOPE        = 'snsapi_login'//'snsapi_base'//'snsapi_userinfo';
     // 这是编码后的地址
    let wxURL = `https://open.weixin.qq.com/connect/qrconnect?appid=${AppID}&redirect_uri=${REDIRECT_URI}&response_type=code&scope=${SCOPE}&state=${STATE}#wechat_redirect`
    //          `https://open.weixin.qq.com/connect/qrconnect?appid=${AppID}&redirect_uri=${return_uri}&response_type=code&scope=SCOPE&state=STATE#wechat_redirect`
    const url = `https://open.weixin.qq.com/connect/qrconnect?appid=${AppID}&redirect_uri=${REDIRECT_URI}&response_type=code&scope=snsapi_login&state=3d6be0a4035d839573b04816624a415e#wechat_redirect`
   // const url = `https://open.weixin.qq.com/connect/qrconnect?appid=${AppID}&redirect_uri=https%3A%2F%2Fpassport.yhd.com%2Fwechat%2Fcallback.do&response_type=code&scope=snsapi_login&state=3d6be0a4035d839573b04816624a415e#wechat_redirect`
  
   
    console.log(wxURL)
    ctx.redirect(wxURL)
    
}


controllers.get_wx_access_token = async(ctx, next)=>{
    //console.log("get_wx_access_token")
    //console.log("code_return: "+req.query.code)
    
    // 第二步：通过code换取网页授权access_token
  
    let {code} = {...ctx.params, ...ctx.query}
    console.log('code....',code)
    request.get(
        {   
            //  `https://api.weixin.qq.com/sns/oauth2/access_token?appid=APPID&secret=SECRET&code=CODE&grant_type=authorization_code`
            url:`https://api.weixin.qq.com/sns/oauth2/access_token?appid=${AppID}&secret=${SECRET}&code=${code}&grant_type=authorization_code`,
        },
           (error, response, body) =>{
            if(response.statusCode == 200){
                
                // 第三步：拉取用户信息(需scope为 snsapi_userinfo)
                //console.log(JSON.parse(body));
                const data = JSON.parse(body);
                const access_token = data.access_token;
                const openid = data.openid;
                
                request.get(
                    {
                       // url:'https://api.weixin.qq.com/sns/userinfo?access_token='+access_token+'&openid='+openid+'&lang=zh_CN',
                          url:`https://api.weixin.qq.com/sns/userinfo?access_token=${access_token}&openid=${openid}&lang=zh_CN`,
                    },
                        (error, response, body)=>{
                        if(response.statusCode == 200){
                            
                            // 第四步：根据获取的用户信息进行对应操作
                            const userinfo = JSON.parse(body);
                            //console.log(JSON.parse(body));
                            console.log('获取微信信息成功！');
                            
                            // 小测试，实际应用中，可以由此创建一个帐户
                            /*
                            res.send("\
                                <h1>"+userinfo.nickname+" 的个人信息</h1>\
                                <p><img src='"+userinfo.headimgurl+"' /></p>\
                                <p>"+userinfo.city+"，"+userinfo.province+"，"+userinfo.country+"</p>\
                            ");
                            */
                           ctx.body = `<h1>${userinfo.nickname} 的个人信息</h1>
                                       <p><img src='${userinfo.headimgurl}' /></p>
                                       <p>${userinfo.city}, ${userinfo.province},${userinfo.country}</p>`
                            
                        }else{
                            console.log(response.statusCode);
                        }
                    }
                );
            }else{
                console.log(response.statusCode);
            }
        }
    );
}
'''

## -----------------


