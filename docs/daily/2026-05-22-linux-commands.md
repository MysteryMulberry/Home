# Linux常用命令速查

## 文件操作
- `find /path -name "*.py"`: 查找文件
- `grep -r "pattern" /path`: 递归搜索
- `du -sh *`: 查看目录大小
- `ln -s target link`: 创建软链接

## 进程管理
- `ps aux | grep python`: 查找进程
- `kill -9 PID`: 强制终止
- `nohup command &`: 后台运行
- `top / htop`: 系统监控

## 网络工具
- `curl -X POST url -d data`: HTTP请求
- `netstat -tlnp`: 查看端口
- `ssh user@host`: 远程连接
- `scp file user@host:path`: 文件传输

## 磁盘管理
- `df -h`: 磁盘使用
- `lsblk`: 块设备列表
- `mount /dev/sda1 /mnt`: 挂载

---
*更新时间: {DATETIME_STR}*
