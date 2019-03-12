#### CSS高级实用技巧
1. 双飞翼布局(css hack)
2. BFC IFC GFC FFC（都是渲染方式的名称）
   + BFC （block formatting content )
   ！每个BFC之间的元素都是独立的 不会发生重叠(也可以解决margin重叠)
   1.哪些元素会生成BFC
        * 根元素
        * float不为none
        * position为absolute或者    fixed
        * display为     inline-block、     inline-flex、flex、       table-cell、       table-caption 
        overflow不为visible
    + 计算BFC元素的高度时 浮动的元素也会参与运算 overflow:hidden;清除原理
    + IFC （inline formatting contexts）
        * 高度尤其包含行内元素中最高的实际高度计算而来（不受垂直方向的padding/margin影响）
    + FFC （flex formatting contexts） display值为flex或者inline-flex的元素将会生成自适应容器
    + GFC （gridlayout formatting contexts）
3. css3 clip-path 裁剪元素 并且支持过渡和动画
4. animation 运动方式 贝塞尔曲线
5. 2D矩阵和3D矩阵
    * 2D矩阵为3\*3 3D矩阵为4\*4
6. transform 操作都是基于matrix实现的
7. transform值的读取顺序是从右往左读
    即 transform: rotate(lutrn)
8. transform: matrix(a,b,c,d,e,f) x,y默认原点为0,0
    + e,f 分别代表水平偏移量和处置偏移量 （设置偏移时其他四个可以任意设置 可以为0）translate
    + a,d 分别代表X轴缩放和Y轴缩放 scale
    + bc 分别代表X轴拉伸和Y轴拉伸 skew