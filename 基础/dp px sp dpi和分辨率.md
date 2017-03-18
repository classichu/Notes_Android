# px像素    【w 1080 h 1920】  【w 720 h 1280】  【w 480 h 800】
pixels  屏幕上的点

# dp(dip)   【w 540 h 960 【w 480 h 640】  【w 480 h 800】
device independent pixels (设备独立像素)  【px/density】
或者（官方文档）
density independent pixel  屏幕密度决定的像素

# sp    【w 540 h 960】  【w 480 h 640】  【w 480 h 800】
scaled pixels  放大像素   【px/scaledDensity】



# dpi    【320】  【240】 【160】
dot per inch  每英寸长度上的点数  单位（像素/英寸）


#分辨率 【1080*1920】  【720*1280】 【480*800】
设备能显示的像素的多少

# in   
英寸  

# pt   
point   磅  1pt＝1/72 英寸

# mm   
毫米  1毫米=1/25.4 英寸

## 屏幕尺寸
屏幕的对角线长度  单位英寸   对角线长度

#DisplayMetrics

### widthPixels   【1080】  【720】 【480】

### heightPixels  【1920】  【1280】 【600】


### density  【2.0】 【1.5】 【1.0】


### densityDpi  【320】 【240】 【160】


### scaledDensity  【2.0】 【1.5】 【1.0】


### xdpi   【72.0】  【72.0】 【72.0】


### ydpi   【72.0】  【72.0】 【72.0】


           dp	          px	     sp	          mm	       in      	pt
ldpi	@ 540.00dp	= 405.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
mdpi	@ 540.00dp	= 540.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
tvdpi	@ 540.00dp	= 718.88px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
hdpi	@ 540.00dp	= 810.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
xhdpi	@ 540.00dp	= 1080.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
xxhdpi	@ 540.00dp	= 1620.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt
xxxhdpi	@ 540.00dp	= 2160.00px	= 540.00sp	= 85.72mm	= 3.38in	= 243.00pt



ldpi	120 dpi
mdpi	160 dpi
tvdpi	213 dpi
hdpi	240 dpi
xhdpi	320 dpi
xxhdpi	480 dpi
xxxhdpi	640 dpi
