# 搭建发布环境

```javascript
npm i pm2 -g
pm2 init//初始化项目运维的脚本环境
pm2 start ecosystem.config.js//启动node服务
pm2 list //查看当前pm2管理的node服务
pm2 restart id(node服务的id)或者ecosystem.config.js//重启
pm2 log //查看日志 
```

