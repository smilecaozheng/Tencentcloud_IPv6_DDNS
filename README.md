# Tencentcloud_IPv6_DDNS
自动更新本机ipv6 通过DNS 解析到公网域名

以下测试环境为ubuntu22.04，环境默认安装python3.10

1.安装crontab：
sudo apt install cron

2.设置crontab为开机启动：
加入开机自动启动：sudo systemctl enable cron   
或者chkconfig –level 35 cron on

3.安装腾讯云API_SDK
pip install -i https://mirrors.tencent.com/pypi/simple/ --upgrade tencentcloud-sdk-python

3.以root用户编辑定时任务
crontab -e

*/10 * * * * python3 /home/klipper/DDNS_v3.py > /home/klipper/DDNS_v3.log
每10分钟运行 输出覆盖文件DDNS.log

查看任务
crontab -l

4.列出root  用户的 list
crontab -u root -l  
# -u 后面是可以选择用户

【crontab的注意事项】
服务相关的命令
sudo systemctl restart cron
service cron start //启动服务
service cron stop //关闭服务
service cron restart //重启服务
service cron reload //重新载入配置
service cron status	//服务状态
