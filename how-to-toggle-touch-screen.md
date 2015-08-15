
# How to toggle the touch screen in Linux?

Just us [`xinput`](http://www.x.org/archive/current/doc/man/man1/xinput.1.xhtml).

List all your devices:

    $ xinput list
    ⎡ Virtual core pointer                    	id=2	[master pointer  (3)]
    ⎜   ↳ Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
    ⎜   ↳ DLL0665:01 06CB:76AD UNKNOWN            	id=12	[slave  pointer  (2)]
    ⎜   ↳ ELAN Touchscreen                        	id=10	[slave  pointer  (2)]
    ⎣ Virtual core keyboard                   	id=3	[master keyboard (2)]
        ↳ Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
        ↳ Power Button                            	id=6	[slave  keyboard (3)]
        ↳ Video Bus                               	id=7	[slave  keyboard (3)]
        ↳ Power Button                            	id=8	[slave  keyboard (3)]
        ↳ Sleep Button                            	id=9	[slave  keyboard (3)]
        ↳ Integrated_Webcam_HD                    	id=11	[slave  keyboard (3)]
        ↳ AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
        ↳ Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

Enable the touch screen with `id=10`:

    xinput enable 10


Source: https://ask.fedoraproject.org/en/question/50590/how-to-disable-touch-screen/
