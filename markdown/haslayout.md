## haslayout
>注：笔记内容大都参考而来，虽然早已找不到作者和翻译着，但还是衷心说声谢谢！
### 什么是haslayout
haslayout是Windows Internet Explorer的一个私有概念，它决定了元素如何对其内容定位和尺寸计算，以及如何与其他元素关系和相互作用。简单来讲，当一个元素“拥有布局”时，它会负责本身以及子元素的尺寸和定位，反之则由最近拥有布局的祖先元素控制。
### 为什么有haslayout
理论来讲，每个元素的定位和尺寸都应该由他自己控制，当然这是理想状态。对于早期的IE来讲，如果每个元素都有自己的布局，性能问题就是一个很大的挑战，所以开发团队决定使用布局来减少性能开销，尽量保证把布局应用到那些实际需要的元素上，所以出现了haslayout，即有无布局的情况。
### 默认拥有布局的元素
```
body and html
table, tr, th, td
img
hr
input, button, file, select, textarea, fieldset
marquee
frameset, frame, iframe
objects, applets, embed 
```
### 如何触发haslayout
除了那些默认会触发的拥有布局的元素外，开发者也可以通过特定css属性来触发haslayout。实际开发中，很多IE下（IE6、IE7）的显示问题，都可以通过触发元素的haslayout来解决，下面列出一些常见的可以触发元素haslayout的属性和方法：
```
float: left或right
display: inline-block
position: absolute
width: 除auto外任何值
height: 除auto外任何值
zoom: 处normal外任何值
writing-mode: tb-rl
```
在IE7中，以下属性也可以触发元素的haslayout
```
min-height: 任意值
min-width: 任意值
max-height: 除none 外任意值
max-width: 除none 外任意值
overflow: 除visible外任意值，仅用于块级元素
overflow-x: 除visible 外任意值，仅用于块级元素
overflow-y: 除visible 外任意值，仅用于块级元素
position: fixed
```
### 引起的bug以及解决办法
- IE常见的浮动bug
- 元素本身对一些基本属性的异常处理
- 相对定位的元素没有布局
- 拥有布局的外边距不叠加
- 等等
综上，一般情况下我们会采用zoom:1;来触发haslayout来解决这些bug，zoom：1；不会影响元素的外在表现，虽然IE5此属性不能触发，但是现在都什么年代了，IE5还是算了吧。还有IE6的早期版本还可以使用height:1%来触发，IE7使用min-height:0触发。
> 既然提到这个，还需要提一下BFC，算了另起一篇吧。
