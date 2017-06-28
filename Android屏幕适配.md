# Android屏幕适配简单总结：
##  * （1）尽量使用自适应宽高尺寸参数-warp_content、match_parent和weight属性
##  * （2）尽量使用相对布局
##  * （3）使用尺寸限定符（参考附图）
##  * （4）屏幕方向限定符（a.land-横屏;  b.port-竖屏）
##  * （5）宽高使用dp，而不是px
##  * （6）把项目中所使用的尺寸，都定义在dimen.xml中统一管理
##  * （7）使用布局别名 
###    (i)我们以res/values/dimens.xml尺寸文件为例，layout等其他文件夹和values同样适用。如下：
``` xml
    <dimen name="width">100dp</dimen>
    <dimen name="width_sw600">600dp</dimen>
```
###    (ii)分别建立res/values-sw600dp/dimens.xml和res/values-large/dimens.xml并写入：
``` xml
    <item name="width" type="dimen">@dimen/width_sw600</item>
```
###    (iii)这样在程序运行中，如果当前手机的宽度大于600dp，则 R.dimen.width = 600dp，否则取值为100dp。
    
##  * （8）最小宽度限定符，在Android 3.2版本引入的（如：values-sw600dp/layout-sw480dp）

# 注：
  尺寸限定符，屏幕方向限定符以及最小宽度限定符可以结合使用！！！
   使用形式如下：
   * res/values-sw600dp-port/
   * res/values-large-land/
  
  
  ![尺寸限定符](/image/android-尺寸限定符.jpg "android尺寸限定符")
