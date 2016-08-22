##BFC(Block Formatting Context)

### What is BFC?
>BFC是W3C CSS 2.1
规范中的一个概念，它决定了元素如何对其内容进行定位，以及与其他元素的关系和相互作用。当涉及到可视化布局的时候，**Block Formatting Context提供了一个环境，HTML元素在这个环境中按照一定规则进行布局**。一个环境中的元素不会影响到其它环境中的布局。
 
要更好地理解BFC，要先来谈谈Box和Formatting Context的概念。我们知道网页布局是由很多盒子组成的，这些块就是Box。元素的类型和 display 属性，决定了这个 Box 的类型。 不同类型的 Box， 会参与不同的 Formatting Context（决定如何渲染文档的格式结构），因此Box内的元素会以不同的方式渲染。

例如：

- block-level box: display 属性为 block, list-item, table 的元素，会生成block-level box。并且参与 block fomatting context；
- inline-level box:display 属性为 inline, inline-block, inline-table的元素，会生成 inline-level box。并且参与 inline ormatting context；  
而Formatting Context是一块渲染区域，它决定了其子元素如何定位，以及与其他元素的位置关系。

根据上述的一些基本概念，我把BFC简单理解成一种属性，在具有BFC属性的容器中，元素按照BFC的规则实现布局。比如浮动元素会形成BFC，这就是为什么我们看到浮动元素布局跟普通文档流下的布局有所差别的原因。 
### 规则是什么呢
- 内部的box会在垂直方向依次放置
- 垂直方向距离由margin决定
- 每个元素的margin box左边和包含块border box的左边相接触(对于由右向左的格式化则相反)，即使浮动也是如此。
- BFC的区域不会与 float box重叠
- BFC 就是页面一个隔离的独立容器，内联元素不会影响外面的元素，反之也如此
- 计算BFC高度时，浮动元素也参与计算
### 哪些元素会生成BFC呢
- 根元素
- 浮动元素，float 属性不为 none
- 绝对定位元素，position为absolute或fixed(fixed是absolute的子类)
- display为inline-block, table-cell, table-caption, flex, - inline-flex
- overflow 不为 visible意外的值
css3中，BFC叫做Flow Root，并增加了一些触发条件
- display 的 table-caption 值
- position 的fixed 值(更加明确了fixed是absolute的子类)
### BFC在布局中的作用
- 解决两元素margin重叠的问题
要想两个相邻的元素不发生垂直方向上的margin重叠，需要将他们两定义在不同的BFC中。解决方法即在其中一个元素外包裹一层元素，再对那层包裹的元素进行BFC触发。（这里可以加入上述的css属性。）
- 解决由于浮动造成的重叠问题
一般情况下，浮动元素会脱离文档流，即不占位置。它的兄弟元素会与它在左上角重叠。但是如果两个相邻元素都设置了浮动，那么意味着它们都是以BFC的规则渲染，根据上述第四条规则，BFC区域不会相互重叠，所以便能理解为什么设置浮动后元素能独占空间了。
- 解决容器由于拥有浮动元素造成高度塌陷的问题
在普通容器中，如果里面有浮动元素，在不设置高度的情况下，容器是不能被撑起来的，这时候通过设置overflow：hidden把其变为BFC，那么就可以包含浮动元素了。
> demo慢慢补
> 
