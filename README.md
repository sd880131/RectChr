# RectChr
Multi-level visualization of genomic statistical variables on rectangular chromosomes

###  1 Introduction
<b>RectChr</b> 

</br>RectChr 主要用于基于Chr染色体水平上多层次的可视工具，对一些统计变量用 点，线，柱状和heatmap、高亮，文本文字， 连接 以及 结合颜色【线，散点，直方图，热图,文本, line, scatter/point, histogram , PairWiseLink，link， heatmap(highlights)和text 】等 可视化各chr上各区域这个统计量，达到快速一眼看出规律，识别结果。  并且各种可以自己组合  自由修改相关参数，使用方法极像circos的一样。
</br>简单点说   circos 可以画的，这儿均可以画，只是把圈圈图改为长方型的。其中自己搭配层颜色等，同时也比circos多了一些默认配置，用起来十分简单，如SNP GC密度 直接输入文件即可。
</br>
</br>程序是给一些有基础的生信朋友用的，若是小白看不懂就算了。
</br>
</br>RectChr is mainly used for muti-Level  visualization tools based on the Chr chromosome level. It uses points, lines, columns and heatmap, highlighting, text text, connection and combined colors for some statistical variables [line, scatter, histogram, heatmap, text , line, scatter/point, histogram, PairWiseLink, link, heatmap (highlights) and text] and so on to visualize the statistics of each area on each chr, so as to quickly see the pattern and recognize the results at a glance. And various parameters can be combined freely to modify related parameters, and the usage method is very similar to circos. To put it simply, circos can be drawn, and all can be drawn here, but the circle diagram is changed to a rectangular shape. Among them, the color of the layer is matched by itself. At the same time, there are some more default configurations than circos, which is very simple to use, such as SNP GC density and input the file directly.


###  2 Download and Install
------------

<b> 2.1. linux/MaxOS&nbsp;&nbsp;&nbsp;   [Download](https://github.com/BGI-shenzhen/RectChr/archive/v1.16.tar.gz)</b>
  
  </br> <b>2.2 Pre-install</b>
  </br> RectChr is for Linux/Unix/macOS only. Before installing, please make sure the following pre-requirements are ready to use.
  </br> 1) Perl : The [SVG.pm](https://metacpan.org/release/SVG) in Perl should be installed. RectChr uses this module to plot figures. We have provided a built-in SVG module in the package.


</br> <b>2.3 Install</b>
</br> Users can install it with the following options:
</br> Option 1: 
<pre>
        git clone https://github.com/BGI-shenzhen/RectChr.git
        chmod 755 -R bin/*
        bin/Rect  -h 
</pre>


###  3 Parameter description
------------
</br><b>3.1 RectChr</b>
</br><b>3.1.1 Main parameter</b>

```php
        Usage: RechChr  -InConfi  in.cofi -OutPut OUT

                -InConfi      <s> : InPut Configuration File
                -OutPut       <s> : OutPut svg file result

                -help               See more help *Manual.pdf
                                    [hewm2008 v1.16]

```
</br> Details for above parameters:
<pre>
	   用法和circos相似，主要一个配置文件一样,具体见pdf
</pre>

</br><b>3.1.2 Other parameters</b>
```php
     输入文件格式见  pdf.主要为chr start end Value1 ... 的格式

```

</br><b>3.2.2 Detail parameters</b>
```php
	具体见pdf
	etParaFor = global

File0  = ./scaf2chr.format2             ##  这个是必须输入参数，并且尽量放在最前,格式为[Chr Start End Value1 Value2 ... ValueN]
                       ##  其中用NA表示不画，chr End End NA不画但End可以用来贝记为chr的长度
ValueX = 2             ##  多少层，类同circos多少个圈，这不设默认是N,即根据File0的格式来的，可以自己设
ChrSpacingRatio =0.2  ##  不同染色体chr之间的间隔比例(ChrWidth*ChrSpacingRatio)
Main = "Scaf2Chr"  ##  the Figtur Name   #font-size  strokewidth=1;  fill="green"

################################ Figure ############################################################



##############################     画布 和 图片 参数配置 #################################
#Chromosomes_order =   ## chr的顺序和只列某些chr出来画，若没有配置，程序会按chr名自动排序 chr1,chr2,chr3
#body=1200   ##   默认是1200，主画布大小设置  另外：up/down/left/right) = (55,25,100,120);
RotatePng   = 90  ##  对Figure进行旋转的角度
RotateChrName  = -90  ##  旋转chr名字 text
#ChrSpacingRatio=0.2    ##  不同染色体chr之间的间隔比例(Sum(ChrWidthX*X)*ChrSpacingRatio)



######    默认各层的配置参数 若各层没有配置的会，则会用这儿的参数 ######

SetParaFor = LevelALL  ##  下面是处理初始化参数 SetParaFor 参数处理,若为 LevelALL，即先为所有层设置的默认值
#File1    =             ##  可以输入别的文件
#PType  = heatmap       ##  线，散点，直方图，热图,文本, line, scatter, histogram ， heatmap(highlights)和text
#ShowColumn =          ##  若SetParaFor为LevelALL时，N层的ShowColumn默认为File0的第ValueN所的Column(N+3)
                       ##  参数格式可以设为 ShowColumn=File0:4 File1:4,5
                       ##  File1:4,5 表示file1的第四和第五列用heatmap表示
#crBegin="#006400"      ##  此层(ValueX)最低值Value 的配色
#crMid="#FFFF00"        ##  此层(ValueX)中间值Value 的配色
#crEnd="#FF0000"        ##  此层(ValueX)最大值Value 的配色
#crGB="#B8B8B8"         ##  此层(ValueX)背景色  的配色
#TopVHigh=0.95          ##  此层Top of ValueX 用最高点颜色[0.95],其它再等分
#TopVLow=0              ##  此层Top of ValueX 用最低点颜色[0],其它再等分
##YMax=                 ##  设置此层(ValueX)的最大值,默认自动
##YMin=                 ##  设置此层(ValueX)的最小值,默认自动
#Gradien=10             ##  此层(ValueX)多少等分颜色
#ChrWidth=20            ##  此层(ValueX)在画布的宽度
#BGWidthRatio =1        ##  此层(ValueX)的背景(backgroup)的宽度默认和ChrWidth一样(0-1])
#LogP=0                 ##  此层(ValueX)不作 0-log10(Value) 处理
#ValueSpacingRatio=0    ##  同一染色体中此层(ValueX)之间的间隔比例(ChrWidth*ValueSpacingRatio)
#SizeGradienRatio=  ##设置渐变条的大小
....  #等等
```

</br><b>3.3 Output files</b>
<pre>
out.svg: Output plot in SVG format
out.png: Output plot in png format
</pre>


###  4 Example
------------

</br>See more detailed usage in the&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>[Chinese Documentation](https://github.com/BGI-shenzhen/RectChr/blob/main/RectChr_Manual_Chinese.pdf)</b>
</br>See more detailed usage in the&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>[English Documentation](https://github.com/BGI-shenzhen/RectChr/blob/main/RectChr_Manual_English.pdf)</b>
</br>See the example directory and  Manual.pdf for more detail.
</br>具体见这儿  Manual.pdf for more detail 里面的实例和配置，后期将在某些网址释放一些教程


</br></br> 
../../bin/RectChr       -InConfi        in.cofi -OutPut OUT 
</br>  目录  Example/example*/　里面有输入和输出和脚本用法。


* Example 1) Sca2chr 示意结果图


![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example1/OUT.png)

* Example 2) 遗传图谱+maker 

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example2/OUT.png)


* Example 3)某一变量的分布图

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example3/OUT.png)


* Example 4)  BinMap+maker的分布图

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example4/OUT.png)


* Example 5)  群体遗传变量+受选择区域


![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example5/OUT.png)


* Example 6) 多个基因组的共线性图 

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example6/OUT1.png)

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example6/OUT4.png)

![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example6/OUT5.png)


* Example 7) 区域link（关联彩虹图）
![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example7/OUT1.png)
![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example7/OUT2.png)


* Example 8) GWAS的图
![out.png](https://github.com/BGI-shenzhen/RectChr/blob/main/Example/example8/OUT.png)


###  5 Advantages

</br>速度快，少内存
</br>可以自我定义组合多层次


###  6 An example image generated by RectChr.
------------

具体实际见程序目录里面的Example/example* 


###  7 Discussing
------------
- [:email:](https://github.com/BGI-shenzhen/RectChr) hewm2008@gmail.com / hewm2008@qq.com
- join the<b><i> QQ Group : 125293663</b></i>

######################swimming in the sky and flying in the sea #############################

