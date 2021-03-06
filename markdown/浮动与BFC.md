##浮动与BFC
上次提到了BFC相关知识，而这次我们来探讨下浮动。在说浮动之前，首先要介绍css可视化模型里面一个非常重要的概念--定位方案。定位方案是控制元素的布局，在css2.1中，有三种定位方案---普通流，浮动和绝对定位。
#### 普通流
普通流中，元素按照其在html中的先后顺序至上而下布局，在这个过程中，行内元素水平排列，直至当前行占满，而块级元素会独占一行。除非另外指定，基本所有元素都是普通流定位，位置由该元素在文档中的文章决定
#### 浮动
浮动布局中，元素首先按照文档流中的位置出现，然后再根据浮动的方向向左右偏移，其实浮动一开始被赋予的意义就是简单的实现文字环绕。
#### 绝对定位
绝对定位布局中，元素整体脱离了普通流，因此不会对其他兄弟元素造成影响，区别于浮动，浮动元素的上下文位置受浮动元素影响。而绝对定位布局元素的位置则由自身的坐标决定。 
   
那么BFC属于哪种呢，之前提到BFC不会对兄弟元素造成影响，所以属于普通流。从样式上来讲具有BFC的元素与普通的容器没啥区别，但是功能上来讲的话，BFC可以看做是被隔离的容器，而且还具有一般容器没有的特效，例如可以包含浮动元素。  

###1.浮动的缺陷
为什么要清除浮动呢？浮动元素方便了我们的页面布局，但同时也会产生一些问题。最为经典的就是，当一个元素设置浮动属性的时候，它会影响兄弟元素的位置并造成父元素高度的塌陷。  
影响兄弟元素的位置还要看兄弟元素是块级元素还是内联元素`此处该有代码以及demo说明`如果是块级元素，会无视掉浮动的元素，最多被覆盖，除非父元素以及兄弟元素设置了宽度。而内联元素的话就会尽可能的围绕浮动元素。  
此外，因为浮动元素脱了了普通流，造成父元素并不会包含浮动元素的高度，所以造成高度塌陷。  
这些都不是浮动的意义，我们需要浮动只是为了实现布局，而不是带来这些负面影响，所以我们要清除浮动带来的影响。
###2.常见方法
提到清除浮动，难免想到clear：both，它有好几个属性来限制当前元素周围的浮动元素。
如果你把浮动元素的兄弟元素设置了clear：both；你会发现并不是你需要的效果，兄弟元素独占一行，而且高度问题还是没解决。这个清除浮动只是解决了浮动对于兄弟元素的影响，父元素高度塌陷还是未解决，所以我们需要更高级的清除浮动----闭合浮动。  
什么是闭合浮动呢？因为浮动元素脱离了普通流，对于父元素来讲并没有闭合，所以这时候就需要闭合浮动了。这个问题经过了这么多年前人的摸索，也有了几个比较完善的方法。
####空div
在我刚接触前端的时候，我就是这么干的(厚着脸皮说)。
在浮动元素后面追加一个空的div 设置clear：both，实现就是这么实现，也灰常的简单，但是仔细一想这个div有啥意义，明显违背了结构表现分离的原则，而且后期维护也不方便。  
####overflow方法
上节介绍的BFC布局就能解决浮动父元素高度塌陷问题。在父元素设置overflow属性为hidden或auto，可以闭合浮动，如果是IE6还需要触发haslayout，为父元素设置高度或者zoom:1。  
这个方法相较与前者方便了不少，但是overflow并不是为了闭合浮动设计的，子元素超出父元素边界时就会出现隐藏或者多余的滚动条，所以此方法还是不够完善。
####after伪元素方法
```
.clearfix{zoom:1;/*haslayout*/}
.clearfix:after{content:"";display: block; height: 0; clear: both; visibility: hidden;}
```
或者
```
.clearfix:before,clearfix:after{display:table;content:"";}
.clearfix{*zoom:1;}
.clearfix:after{clear:both;}
```
###3.清除浮动的实质
通过以上，我们不难发现清除浮动的方法可以分成两类：
一种是通过浮动元素末尾添加clear：both为空的div，：after为元素方法实际也是如此实现
第二种是通过触发父元素的BFC，使父元素可以包含浮动元素。（BFC笔记请移步上一节）


