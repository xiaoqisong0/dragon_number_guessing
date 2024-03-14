# 1.上线流程

## 1.1.修改数据库配置

修改application-druid.yml中的数据库配置为生产配置


![./readmeAttachments/1-deploy-1.png](./readmeAttachments/1-deploy-1.png)

## 1.2.修改vue的接口请求路径


修改/ruoyi-ui下的.env.production文件的VUE_APP_BASE_API
为：

https://xyzadmin.xyzpgc.com/ruoyi-admin

![./readmeAttachments/1-deploy-2.png](./readmeAttachments/1-deploy-2.png)

## 1.3.备份

* 备份线上数据库脚本
* 备份生产环境的war包
* 备份生产dist下的html文件


## 1.4.执行SQL脚本

* 执行比对后的SQL脚本，更新线上数据库
* 注意添加菜单和角色权限

## 1.5.打包新版本

打包新的版本包，并将war包名称改为

**ruoyi-admin.war**


## 1.6.通过ssh发布新的war包

java部署路径为：

/usr/local/java/tomcat8.5/webapps

vue部署路径为：

/usr/local/java/tomcat8.5/webapps/dist

**注意不要删除dist下的 WEB-INF**

## 1.7.上线后验证

* 后台管理系统是否正确