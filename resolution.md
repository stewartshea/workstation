# Adding more resolution options
Not sure this should be codified since it's machine dependent. Wayland provided many screen options, but Xorg only gave one for the Huawei machine which is too high for most normal work and the "scale" option seems to apply to every monitor, making lower res monitors unusable due to too much scale. 

- Get displays
```
$ xrandr -q
Screen 0: minimum 320 x 200, current 3000 x 2000, maximum 8192 x 8192
eDP-1 connected primary 3000x2000+0+0 (normal left inverted right x axis y axis) 293mm x 196mm
   3000x2000     60.00*+  48.01  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
```
- Calculate options
```
$ cvt 1920 1200
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
$ cvt 2560 1600
# 2560x1600 59.99 Hz (CVT 4.10MA) hsync: 99.46 kHz; pclk: 348.50 MHz
Modeline "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
```
- Create options for the main display
```
$ xrandr --newmode "1920x1200_60.00" 193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
$ xrandr --newmode "2560x1600_60.00" 348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
$ xrandr --addmode eDP-1 "1920x1200_60.00"
$ xrandr --addmode eDP-1 "2560x1600_60.00"
```

# Resources
Excellent help found here: 
- [https://unix.stackexchange.com/questions/292714/bad-resolution-on-second-monitor-fedora-24](https://unix.stackexchange.com/questions/292714/bad-resolution-on-second-monitor-fedora-24)