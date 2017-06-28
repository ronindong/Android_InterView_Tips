# Android屏幕适配总结：
##  * （1）尽量使用自适应宽高尺寸参数-warp_content、match_parent和weight属性
##  * （2）尽量使用相对布局
##  * （3）使用尺寸限定符（参考附图）
##  * （4）屏幕方向限定符（a.land-横屏;  b.port-竖屏）
##  * （5）宽高使用dp，而不是px
##  * （6）把项目中所使用的尺寸，都定义在dimen.xml中统一管理
##  * （7）使用布局别名（）
##  * （8）最小宽度限定符（如：values-sw600dp/layout-sw480dp）

# 注：
  尺寸限定符，屏幕方向限定符以及最小宽度限定符可以结合使用！！！
   使用形式如下：
   * res/values-sw600dp-port/
   * res/values-large-land/
  
  
  ![尺寸限定符](/image/android-尺寸限定符.jpg "android尺寸限定符")
