# Linux CentOS7 防火墙

```Linux
# 安装firewalld
yum install firewalld firewall-config

systemctl start  firewalld # 启动
systemctl stop firewalld  # 停止
systemctl enable firewalld # 启用自动启动
systemctl disable firewalld # 禁用自动启动
systemctl status firewalld # 或者 firewall-cmd --state 查看状态
```

## systemctl 指令说明

| 任务                 | 旧指令                        | 新指令                                                                                                 |
| -------------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------ |
| 使某服务自动启动     | chkconfig --level 3 httpd on  | systemctl enable httpd.service                                                                         |
| 使某服务不自动启动   | chkconfig --level 3 httpd off | systemctl disable httpd.service                                                                        |
| 检查服务状态         | service httpd status          | systemctl status httpd.service （服务详细信息） systemctl is-active httpd.service （仅显示是否 Active) |
| 显示所有已启动的服务 | chkconfig --list              | systemctl list-units --type=service                                                                    |
| 启动服务             | service httpd start           | systemctl start httpd.service                                                                          |
| 停止服务             | service httpd stop            | systemctl stop httpd.service                                                                           |
| 重启服务             | service httpd restart         | systemctl restart httpd.service                                                                        |
| 重载服务             | service httpd reload          | systemctl reload httpd.service                                                                         |
