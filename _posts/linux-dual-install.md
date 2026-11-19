---
title: Linux Dual Install
date: 2014-08-04 10:23:09
tags: 
  - Linux
  - Windows
---

# Linux 安装配置

记录下 Linux 操作系统的安装与配置技巧。

## 1️. 屏幕亮度调节（笔记本）

在 Grub2 的命令中添加以下参数之一，可启用功能键调节亮度：

- `acpi_osi=Linux`
- `acpi_backlight=vendor`
- `acpi_osi="!Windows 2012"`

修改 `/etc/default/grub` 文件：

```bash
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```

然后运行：

```bash
sudo update-grub
```

也可使用 Grub2-config 工具进行图形化修改。

## 2. 设置 Windows 安装分区为激活状态（双系统）

安装顺序建议：先 Windows → 后 Linux  
确保 Grub2 成为主引导器，并设置 Windows 分区为激活状态。

在 `/etc/grub.d/30_os-prober` 中的 Windows 条目添加：

```bash
parttool (hd0,msdos2) boot+  # 设置 Windows 分区为启动分区
```

完整启动项示例中插入该行后运行：

```bash
sudo update-grub
```

可解决 Windows 更新无法识别启动分区的问题。

## 3. 自动挂载 NTFS 分区

安装 `ntfs-3g`：

```bash
sudo apt install ntfs-3g
```

编辑 `/etc/fstab` 添加挂载项：

```bash
/dev/sda5 /media/Documents ntfs-3g defaults,locale=zh_CN.UTF-8 0 0
/dev/sda6 /media/Musics    ntfs-3g defaults,locale=zh_CN.UTF-8 0 0
/dev/sda7 /media/Videos    ntfs-3g defaults,locale=zh_CN.UTF-8 0 0
```

确保挂载点目录已创建。

## 4. 禁用服务开机自启动（如 Apache2、MySQL）

安装 `sysv-rc-conf` 工具：

```bash
sudo apt install sysv-rc-conf
sudo sysv-rc-conf
```

手动修改配置文件（以 MySQL 为例）：

编辑 `/etc/init/mysql.conf`：

```bash
start on runlevel [2345]   # 删除不希望启动的 runlevel
stop on starting rc RUNLEVEL=[016]  # 可添加 runlevel 来阻止启动
```

也可使用 `service mysql start` 手动启动服务。

