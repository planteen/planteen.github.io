---
layout: post
title: Linux on ZenBook UX501
date: 2017-02-10
categories: Linux
---

I was previously using a lower end System76 laptop. It was nice to have 
guaranteed Linux compatibility, but the build quality left something to be
desired. So I decided on a Asus ZenBook Pro UX501 for my new laptop. The case
is metal and I liked the specs - 4K display, 16 GB RAM, quad core i7 CPU, and a
GTX960M GPU.

I knew getting Linux running might be a little tricky. My fears were confirmed -
Ubuntu 16.10 hung immediately upon starting graphics. I found a
[page from Arch](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Pro_UX501)
that suggested some kernel boot parameters. It still hung. I considering
installing Arch, but I wasn't sure I was ready for the commitment. So I tried
Fedora 25 with the same parameters first. The live session was stable so I
installed to disk. The key is to edit the boot parameters (press e) before the
Linux installer boots and append `i915.enable_execlists=0 acpi_osi=! acpi_osi="Windows 2009"`

Once the system is installed, edit `/etc/default/grub` to permanently fix the kernel boot parameters. Otherwise, every time the kernel is updated, you are going to have to re-edit your grub configuration. On `GRUB_CMDLINE_LINUX`, I deleted `rhgb quiet` as a matter of preference. I then appended `i915.enable_execlists=0 acpi_osi=! acpi_osi=\"Windows 2009\"` (notice that you need to escape the quotes). I also added the following options so Fedora will always boot to the last OS that was selected. This is useful if you are dual booting.

```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

Now, rewrite the grub loder configuration
`sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg`

There is complexity due to the fact there are 2 GPUs (NVIDIA and Intel). To
handle this I installed bumblebee. There are good directions on the
[Fedora page](https://fedoraproject.org/wiki/Bumblebee) for that.

The only piece of hardware that doesn't seem to work is the built-in SD card
reader:

```
$ lspci | grep -i alcor
02:00.0 Unassigned class [ff00]: Alcor Micro Device 6621
```

The HiDPI display support in Linux is pretty good, until you mix in an external
monitor that is a lower DPI (like a 24" 1080p monitor). Lots of applications
show windows zoomed way too much on the low DPI monitor. But luckily
gnome-terminal, my most used app, works flawless between different DPI
monitors. Overall, I am pleased.
