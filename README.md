Microtouch input driver modified to work with a specific, older touchscreen model.

Forked from: https://gitlab.freedesktop.org/xorg/driver/xf86-input-mutouch

As the driver doesn't support automatic device recognition and has to be configured
in the `xorg.conf` file, here is an excerpt with the required sections, assuming
the driver was installed to the `/usr/local/' prefix (which is default).

```
Section "ServerLayout"
    # ...
    # Only this part is required, but usually the whole layout has
    # to be specified here as well.
    InputDevice    "MuTFinger"
    # ...
EndSection

Section "Files"
    # Let Xorg find both distribution modules and the admin-installed modules
    ModulePath "/usr/lib64/xorg/modules,/usr/local/lib/xorg/modules"
EndSection

Section "Module"
    Load           "mutouch"    
EndSection

# MicroTouch touchscreen section
Section "InputDevice"
    Identifier          "MuTFinger"
    Driver              "mutouch"
    Option "MinX"       "0"
    Option "MaxX"       "16383"
    Option "MinY"       "0"
    Option "MaxY"       "16383"
    Option "SwapXY"     "1"
    Option "DebugLevel" "3"
    Option              "Type" "finger"
    Option              "Device" "/dev/ttyUSB0"
    Option              "PortraitMode" "Landscape"
EndSection
```

==================================================================================

xf86-input-mutouch - Microtouch input driver for the Xorg X server

Please submit bugs & patches to the Xorg bugzilla:

        https://bugs.freedesktop.org/enter_bug.cgi?product=xorg

All questions regarding this software should be directed at the
Xorg mailing list:

        http://lists.freedesktop.org/mailman/listinfo/xorg

The master development code repository can be found at:

        git://anongit.freedesktop.org/git/xorg/driver/xf86-input-mutouch

        http://cgit.freedesktop.org/xorg/driver/xf86-input-mutouch

For more information on the git code manager, see:

        http://wiki.x.org/wiki/GitPage
