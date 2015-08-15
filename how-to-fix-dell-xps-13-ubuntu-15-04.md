# How to fix Dell XPS 13 (2015) for Ubuntu 15.04

# Suspend error

Download https://launchpadlibrarian.net/207055396/lp1415880.debdiff

And then do:

    sudo apt-get install build-essential fakeroot devscripts
    sudo apt-get source bcmwl-kernel-source
    sudo apt-get build-dep bcmwl-kernel-source
    cd bcmwl-6.30.223.248+bdcom/
    sudo patch -p1 < ~/lp1415880.debdiff
    sudo debuild -uc -us
    sudo dpkg -i ../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu3_amd64.deb

Source: https://github.com/advancingu/XPS13Linux/issues/13

# Bluetooth problems

I was getting this error:

    Aug 15 14:07:24 kiki kernel: ------------[ cut here ]------------
    Aug 15 14:07:24 kiki kernel: WARNING: CPU: 2 PID: 4302 at /build/linux-OdodyZ/linux-3.19.0/drivers/base/firmware_class.c:1126 _request_firmware+0x72e/0xbd0()
    Aug 15 14:07:24 kiki kernel: Modules linked in: nvram msr binfmt_misc rfcomm bnep dm_crypt nls_iso8859_1 dell_wmi sparse_keymap intel_rapl iosf_mbi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel dell_laptop dcdbas kvm wl(POE) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper joydev cryptd serio_raw uvcvideo hid_multitouch videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common dell_led videodev media snd_hda_codec_realtek btusb snd_hda_codec_generic bluetooth snd_hda_codec_hdmi cfg80211 rtsx_pci_ms memstick lpc_ich shpchp mei_me snd_soc_rt286 mei snd_hda_intel snd_soc_core snd_hda_controller snd_compress snd_hda_codec snd_pcm_dmaengine snd_hwdep snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore
    Aug 15 14:07:24 kiki kernel:  i2c_hid int3403_thermal soc_button_array dw_dmac snd_soc_sst_acpi i2c_designware_platform dw_dmac_core 8250_dw i2c_designware_core spi_pxa2xx_platform int3402_thermal processor_thermal_device int3400_thermal acpi_thermal_rel mac_hid acpi_pad parport_pc ppdev lp parport autofs4 usbhid hid rtsx_pci_sdmmc i915 psmouse i2c_algo_bit ahci drm_kms_helper libahci drm rtsx_pci wmi video sdhci_acpi sdhci
    Aug 15 14:07:24 kiki kernel: CPU: 2 PID: 4302 Comm: kworker/u9:0 Tainted: P           OE  3.19.0-25-generic #26-Ubuntu
    Aug 15 14:07:24 kiki kernel: Hardware name: Dell Inc. XPS 13 9343/0310JH, BIOS A05 07/14/2015
    Aug 15 14:07:24 kiki kernel: Workqueue: hci0 hci_power_on [bluetooth]
    Aug 15 14:07:24 kiki kernel:  ffffffff81b122c0 ffff8802128fbb78 ffffffff817c4518 ffffffff81c54eb8
    Aug 15 14:07:24 kiki kernel:  0000000000000000 ffff8802128fbbb8 ffffffff81076a6a ffffffff8151aeca
    Aug 15 14:07:24 kiki kernel:  ffff8802128fbcd0 ffff8800d8b0a600 ffff8800d867ae40 00000000fffffff5
    Aug 15 14:07:24 kiki kernel: Call Trace:
    Aug 15 14:07:24 kiki kernel:  [<ffffffff817c4518>] dump_stack+0x45/0x57
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81076a6a>] warn_slowpath_common+0x8a/0xc0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff8151aeca>] ? _request_firmware+0x5a/0xbd0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81076b5a>] warn_slowpath_null+0x1a/0x20
    Aug 15 14:07:24 kiki kernel:  [<ffffffff8151b59e>] _request_firmware+0x72e/0xbd0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff8151ba75>] request_firmware+0x35/0x50
    Aug 15 14:07:24 kiki kernel:  [<ffffffffc053abe9>] btusb_setup_bcm_patchram+0x89/0x570 [btusb]
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81512746>] ? rpm_idle+0xd6/0x230
    Aug 15 14:07:24 kiki kernel:  [<ffffffffc06ba561>] hci_dev_do_open+0xe1/0xa90 [bluetooth]
    Aug 15 14:07:24 kiki kernel:  [<ffffffffc06bb6f0>] hci_power_on+0x40/0x200 [bluetooth]
    Aug 15 14:07:24 kiki kernel:  [<ffffffff8108fd58>] process_one_work+0x158/0x430
    Aug 15 14:07:24 kiki kernel:  [<ffffffff8109089b>] worker_thread+0x5b/0x530
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81090840>] ? rescuer_thread+0x3a0/0x3a0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81095939>] kthread+0xc9/0xe0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81095870>] ? kthread_create_on_node+0x1c0/0x1c0
    Aug 15 14:07:24 kiki kernel:  [<ffffffff817cb518>] ret_from_fork+0x58/0x90
    Aug 15 14:07:24 kiki kernel:  [<ffffffff81095870>] ? kthread_create_on_node+0x1c0/0x1c0
    Aug 15 14:07:24 kiki kernel: ---[ end trace 8b5f93bcf5a27ec8 ]---
    Aug 15 14:07:24 kiki kernel: bluetooth hci0: firmware: brcm/BCM20702A0-0a5c-216f.hcd will not be loaded
    Aug 15 14:07:24 kiki kernel: Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0a5c-216f.hcd not found

Download http://catalog.update.microsoft.com/v7/site/ScopedViewRedirect.aspx?updateid=87a7756f-1451-45da-ba8a-55f8aa29dfee

Compile `hex2hcd` from https://github.com/jessesung/hex2hcd and then do this:

      cabextract 20662520_6c535fbfa9dca0d07ab069e8918896086e2af0a7.cab
      hex2hcd BCM20702A1_001.002.014.1443.1572.hex
      sudo mv BCM20702A1_001.002.014.1443.1572.hcd /lib/firmware/brcm/BCM20702A1-0a5c-216f.hcd
      sudo ln -rs /lib/firmware/brcm/BCM20702A1-0a5c-216f.hcd /lib/firmware/brcm/BCM20702A0-0a5c-216f.hcd


Source: https://wiki.archlinux.org/index.php/Dell_XPS_13_%282015%29#Bluetooth

# Install TLP

    sudo add-apt-repository ppa:linrunner/tlp
    sudo apt-get update 
    sudo apt-get install tlp tlp-rdw 
