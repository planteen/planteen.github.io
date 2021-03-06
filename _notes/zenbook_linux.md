Linux on ZenBook UX501
======================

Ubuntu hangs on my ZenBook with the default configuration.
I found a
[page from Arch](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Pro_UX501)
that suggested some kernel boot parameters. Ubuntu still hung. Fedora 29 boots with the parameters. The live session was stable so I
installed to disk. The key is to edit the boot parameters (press e) before the
Linux installer boots and append `i915.enable_execlists=0 acpi_osi=! acpi_osi="Windows 2009"`

Once the system is installed, edit `/etc/default/grub` to permanently fix the kernel boot parameters. Otherwise, every time the kernel is updated, you are going to have to re-edit your grub configuration. On `GRUB_CMDLINE_LINUX`, I deleted `rhgb quiet` as a matter of preference. I then appended `i915.enable_execlists=0 acpi_osi=! acpi_osi=\"Windows 2009\"` (notice that you need to escape the quotes). I also added the following options so Fedora will always boot to the last OS that was selected. This is useful if you are dual booting.

```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

Now, rewrite the grub loder configuration
`sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg`
