本项目是由 PHP研究院：Q群【 200979897 】

推出的基于PHP7+Swoole+Redis+Mysql实现的实时聊天系统

CharRoom单词写错了，有洁癖的自行修改


#每天凌晨 4点 重启各种服务器
5  4 * * * service php-fpm restart  >/dev/null 2>&1 &

10 4 * * * service nginx restart  >/dev/null 2>&1 &

15 4 * * * service mysql restart  >/dev/null 2>&1 &

20 4 * * * service redis restart  >/dev/null 2>&1 &

# 每5分钟监控牌局server
*/5 * * * * cd /var/www/html/poker && php think Swoole -m "monitor"  >/dev/null 2>&1 &

# 每5分钟
*/5 * * * * cd /var/www/charRoom  && php think Swoole -m "monitor"  >/dev/null 2>&1 &

# 每小时执行一次 重启一下worker
1 * * * *  cd /var/www/charRoom  && php think Swoole -m "reload"  >/dev/null 2>&1 &

#每天凌晨两点
0  2 * * * cd /var/www/html/wangSanBaErA &&  php think  CreateTable >/dev/null 2>&1 &


