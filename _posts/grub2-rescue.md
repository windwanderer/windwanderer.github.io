---
title: Grub2 Rescue
date: 2014-08-04 14:24:05
tags: 
  - Linux
  - Grub
---

# GRUB2 Rescue 模式时使用的开机命令

## 背景说明

当使用 Grub2 作为启动管理器时，如果配置错误或安装失败，系统可能会进入 `grub-rescue>` 模式，而不是显示正常的启动菜单。此时需要手动输入命令来启动操作系统。

此外，在正常 Grub2 启动菜单界面下，按下 `c` 键可进入命令行模式，提示符为 `grub>`。

## 查看当前 Grub2 设置

```bash
set       # 显示当前 Grub2 环境变量
ls        # 查看识别到的设备，如 (hd0), (hd0,1), (hd0,msdos2)
```

## 快速启动最近的内核

```bash
set root=(hd0,msdos1)              # 设置根分区
insmod /boot/grub/linux.mod        # grub-rescue 模式下需加载 linux 模块
linux /vmlinuz root=/dev/sda1 ro   # 加载内核并指定根分区
initrd /initrd.img                 # 加载 initrd 镜像
boot                               # 启动系统
```

> 注意：`insmod` 仅在 `grub-rescue>` 模式下需要，正常 `grub>` 模式可省略。

## 启动指定版本内核

```bash
set root=(hd0,msdos1)
insmod /boot/grub/linux.mod
linux /boot/vmlinuz-3.2.0-67-generic root=/dev/sda1 ro
initrd /boot/initrd.img-3.2.0-67-generic
boot
```

> 提示：输入路径时可使用 Tab 键自动补全，如 `/boot/vml` 后按 Tab 补全内核文件名。

参考链接：[GRUB 2 中文指南](http://wiki.ubuntu-tw.org/index.php?title=Grub2)

## 总结

- `grub-rescue>` 模式下需手动加载模块
- 使用 `set` 和 `ls` 确认设备与分区
- 正确设置 `root`、加载内核与 initrd 后执行 `boot`
- Tab 补全功能可加快路径输入
