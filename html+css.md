## HTML+CSS
### HTML5语义化
利用有意义的标签来构建网页，更好地描述页面的结构与用途，提高代码的可读性和可维护性，改善搜索引擎的优化和可访问性。  
HTML5的语义化标签包括header、footer、article、aside等等
### HTML5的新特性
1. 新的语义元素
2. 增强表单控件，新的一些输入类型：email、date、range，一些属性：placeholder、required
3. 新的存储方式：localStorage：无过期时间，sessionStorage：存储会话数据，浏览器关闭清除
4. 提供获取地理位置的api
5. 提供websockets协议，用于建立通信
### 渐进增强与优雅降级
定义一个基准线，在此之上叫做渐进增强，利用css优化体验，在此之下的叫做优雅降级，利用html语义化的功能，即使在js/css禁用时也不会影响功能。
### CSS3新特性
#### 动画
```css
@keyframes 动画名称{
	from{
	
	}
	to{
	
	}
}
//在想要动画的标签上加上animation:动画名称
```
#### 过渡(一般配合:hover使用)
css的一个属性
```css
  .box {
    width: 100px;
    height: 100px;
    background-color: red;
    transition: all 1s;
  }

  .box:hover {
    width: 200px;
    background-color: blue;
  }
```
这段代码展示了过渡的使用，鼠标悬停时，在0.5s的时间内，宽度从100->200，背景从red->blue
#### 形状转换 transfrom
面对这个属性的时候，主要有一下四种操作方式
```css
  .rotate {
    transform: rotate(45deg);
  }
//旋转
  .scale {
    transform: scale(1.5);
  }
//放大放小
  .translate {
    transform: translate(50px, 50px);
  }
//移动
  .skew {
    transform: skew(20deg, 20deg);
  }
//倾斜
```
#### nth-of-type选择器
```css
p:nth-child(2)//匹配到第二个元素，这个元素必须是p，不然就不匹配
p:nth-of-type(2)//匹配到第二个p元素
```
#### flex布局
```css
  .container {
    display: flex;//flex创建块级弹性布局，inline-flex创建行内弹性布局
    flex-direction: row;//主轴方向row为从左到右，row-reverse从右到左，column为从上到下，column-reverse为从下到上。
    flex-wrap: wrap;//nowrap是不换行，wrap是换行，wrap-reverse是以wrap相反的方向排
    justify-content: space-around;//控制元素在主轴上的排列，flex-start向项目的起始位置靠齐，flex-end向项目的结束位置靠齐，center位于项目中间，space-between平均分布在主轴线上，第一个元素在起始位置，最后一个在结束位置，其余的元素分布在这两个元素之间，间距相等，space-around相当于每个元素都加了一个左右的边框，第一个元素的左边和最后一个元素的右边距离边框的距离是其余的一半
    align-items: center;//控制元素在交叉轴上的排列，flex-start向项目的起始位置靠齐，flex-end向项目的结束位置靠齐，center位于项目中间，baseline，向项目的基线（第一行文字的底部）对齐，stretch，拉伸元素直至充满交叉轴的空间
    align-content: space-between;//控制在多根主轴的情况下，这些主轴在交叉轴上的排列方式（当flex-wrap为wrap或wrap-reverse时才会生效）前5个值与justify-content相同，还有一个值为stretch，轴线被拉伸充满交叉轴
    height: 400px;
    border: 2px solid #ccc;
  }
  .item {
    background-color: lightblue;
    padding: 20px;
    margin: 10px;
    flex: 1 1 100px; /* flex-grow: 1, flex-shrink: 1, flex-basis: 100px */
  }
  //对于每一个在弹性容器里面的元素，flex-grow表示有剩余空间时，元素分配剩余空间的能力，0为不分配即项目不会放大，如果都为0，则会平均分配剩余的空间，如果为其他数字表示放大比例。
  //flex-shrink表示空间不够的时候，元素收缩的能力，默认为1，即自动收缩，如果大于1，其他元素为1，则前者会收缩的更厉害。
  //flex-basis表示项目占据的主轴空间，默认为auto即根据项目的内容决定。
```
#### 媒体查询
```css
@media screen and(max-width:992px){
	color:blue
}
```
### css盒子模型
标准盒子：在宽度之外再绘制盒子的内边距和border，即总宽度=width+padding（左右都算）+border（左右）+margin  ，通过box-sizing:content-box控制
怪异盒子：width已经包括了padding（左右都算）+border（左右），即总宽度=width+margin（左右），通过box-sizing:border-box控制
### 如何使一个行内的元素水平居中
1. 外面包一个块级元素，在这个块级元素上加上text-align:center
2. 外面包一个块级元素，让这个块级元素服从flex布局，并让内容展示在中间，即加上
```css
.father{
	display:flex
	justify-content:center
}
```
### 如何使一个块级元素水平居中
1. 在宽度width存在的情况下，使用margin:0 auto即可搞定
2. 同样是宽度确定的情况下，使用子绝父相，给子元素设置margin-left:(父宽-子宽)/2
3. 不晓得宽度可以转成行内块，然后外面包一个块级元素，在这个块级元素上加上text-align:center
4. 绝对定位加translateX(-50%)
```css
.centered-block {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
}
```
5. flex布局，同行内第二条方法
### 如何垂直居中
1. flex布局，注意父级容器需要把高度调到合适高度
```css
<div class="test2"><div class="test1">This is a test HTML file.</div></div>
    .test2 {
        display: flex;
        align-items: center;
        height: 100vh;
    }
    .test1 {
        margin:auto;
    }
```
2. 子绝父相实现，原理类似于 ### 如何使一个块级元素水平居中的4
### 隐藏页面中某个元素的方法

1.`opacity：0`，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定 一些事件，如click 事件，那么点击该区域，也能触发点击事件的

2.`visibility：hidden`，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已 经绑定的事件 ，隐藏对应元素，在文档布局中仍保留原来的空间（重绘）

3.`display：none`，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素。 不显示对应的元素，在文档布局中不再分配空间（回流+重绘）
#### 回流和重绘
回流和重绘都是浏览器在渲染页面时的重要过程  
回流：当元素的几何属性（位置，尺寸，边距）等等发生变化时，浏览器重新计算页面中元素中的位置和布局的过程，开销大  
重绘：元素的样式属性（颜色，背景色）发生变化时，浏览器重新绘制元素外观的过程，开销小  
总体来说，二者都会影响页面的性能，提出以下建议减少发生次数：
1. 减少dom访问，少使用一些offsetHeight类似的访问尺寸的元素
2. 批量修改样式，减少次数
3. 最小化重排区域，尽量避免在面积布局大的元素上频繁进行操作
### 如何清除浮动
1. 父元素加属性overflow: hidden
2. 使用空div清除
```css
.clearfix::after {
    content: "";
    display: table;
    clear: both;
}
```
3. 父级加高度
4. flex布局