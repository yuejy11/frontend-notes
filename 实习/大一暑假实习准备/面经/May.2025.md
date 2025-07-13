## 2025.5

#### 1.说一说样式优先级的规则是什么

优先级：也叫权重，当一个标签使用了多种选择器时，基于不同种类的选择器的匹配规则

规则：选择器优先级高的样式生效

**公式：通配符选择器 < 标签选择器 < 类选择器 < id选择器 < 行内样式 < !important**

**（选中的标签范围越大，优先级越低）**

**优先级 - 叠加运算规则：**

叠加运算：如果是复合选择器，则需要权重叠加计算（每一级之间不存在进位）

**（行内样式，id选择器个数，类选择器个数，标签选择器个数）**

规则：

+ 从左向右依次比较个数，同一级个数多的优先级高，如果个数相同，则向后比较
+ !important 权重最高
+ 继承权重最低

例1：

```css
<div id="box1" class="c1">
	<div id="box2" class="c2">
		<div id="box3" class="c3">
			这行文字是橙色的
		</div>
	</div>
</div>

/* (0,0,2,1) */
.c1 .c2 div {
    color: blue;
}
/* (0,1,0,1) */
div #box3 {
    color: green;
}
/* (0,1,1,0) */
#box1 .c3 {
    color: orange;
}
```

例2：

```css
<div class="father">
	<p class="son">
		这行文字是红色的
	</p>
</div>

div p {
    color: red;
}
/* 继承权重最低 */
.father {
    color: blue;
}
```

例3：

```css
<div id="father" class="c1">
	<p id="son" class="c2">
		这行文字是蓝色的
	</p>
</div>

/* (0,2,0,0) */ 
#father #son {
    color: blue;
}
/* (0,1,1,1) */
#father p .c2 {
    color: black;
}
/* (0,0,2,2) */
div .c1 p .c2 {
    color: red;
}
/* !important权重最高，但是样式设置给了父级，继承权重最低 */
#father {
    color: green !important;
}
/* 样式设置给了父级，继承权重最低 */
div #father .c1 {
    color: yellow;
}
```

#### 2.说一说css尺寸设置的单位

常见的css尺寸设置单位包括像素（px）、百分比（%）、em、rem、vw / vh

+ 像素（px）：

  简单理解像素就是屏幕上最小的一个显示单元，就相当于画画时那一个小点点，像素分为两种类型：css像素 和 物理像素

  + css像素：专门为开发者提供，在css中使用的一个抽象单位，就是我们在写样式的时候，比如 `width:100px` 中的 px
  + 物理像素：物理像素指的是屏幕上真实存在的小方块数量，一个css像素最终呈现在屏幕上可能是多个物理像素，也就是 DPR

+ 百分比（%）：相对于父元素的尺寸

+ em 和 rem：

  + em：相对于父元素的字体大小  1em = 父元素的 font-size
  + rem：相对于根元素的字体大小（html元素的 font-size） 1rem = html的font-size 

+ vw / vh：

  + vw：相对视口宽度  1vw = 视口宽度的1%
  + vh：相对视口高度  1vh = 视口高度的1%

  > 视口：显示HTML网页的区域，用来约束HTMl尺寸

#### 3.说一说BFC

BFC就是块格式化上下文（Block Formatting Context），简单来说就是网页中的一个独立布局环境（BFC是一个区域）。在这个环境里面的元素布局不会影响到外面的元素，外面的元素也不会影响到它。常见的触发方式是 `overflow: hidden`

**创建BFC的条件：**

+ <body>  和  <html>根元素
+ **元素设置浮动：float 除了 none 以外的值**
+ 元素定位：position 设为 absolute 或 fixed（这两个会脱标）
+ display 值为：flow-root、flex、inline-block
+ overflow 值为：**hidden**、auto

**BFC的特点：**

+ 垂直方向上，自上而下排列，和文档流的排列方式一致

+ 在BFC中上下相邻的两个容器的margin会重叠（外边距合并问题的原因）

+ BFC区域不会与浮动的容器（也是一个BFC区域）发生重叠

+ BFC是独立的容器，容器内部元素不会影响外部元素

+ 计算BFC高度时，子元素的margin也参与计算（解决外边距塌陷问题）

  > 也就是元素触发BFC后，其中的浮动子元素也被包含在内

**BFC的作用：**

+ **解决外边距合并问题：**给其中一个盒子设置 overflow: hidden ，创建BFC且包裹了该盒子，与另外一个盒子隔离，解决了合并问题

+ **清除浮动：**给父元素设置 overflow: hidden ，其中的浮动子元素也被包含在内，父元素的高度就由浮动子元素撑开

+ **创建自适应两栏布局：**左边宽度固定，右边宽度自适应

  ```css
  <div class="container">
  	<div class="left"></div>
  	<div class="right"></div>
  </div>

  .container {
      width: 300px;
      height: 300px;
      background-color: skyblue;
  }
  .container .left {
      width: 100px;
      height: 100px;
      background-color: red;
  }
  .container .right {
      /* 创建BFC，BFC区域不会与浮动元素重叠 */
      overflow: hidden;
      height: 300px;
      background-color: green;
  }
  ```

#### 4.两栏布局的实现

一般两栏布局指的是**左边一栏宽度固定，右边一栏宽度自适应**，两栏布局的具体实现：

+ **flex布局（推荐）**

  ```css
  <div class="container">
    <div class="left">左边固定</div>
    <div class="right">右边自适应</div>
  </div>

  .container {
   	display: flex;
      height: 100px;
  }

  .left {
    	height: 100px;
    	width: 200px;
    	background: skyblue;
  }

  .right {
    	flex: 1;
      height: 100px;
    	background: orange;
  }
  ```

+ float+ margin



#### 5.三栏布局的实现

三栏布局一般指的是页面中一共有三栏，**左右两栏宽度固定，中间自适应的布局**，三栏布局的具体实现：

+ **flex布局（推荐）**

  ```css
  <div class="container">
    <div class="left">左栏</div>
    <div class="center">中间栏</div>
    <div class="right">右栏</div>
  </div>

  .container {
    	display: flex;
    	height: 100px;
  }

  .left {
    	width: 200px;
      height: 100px;
    	background: skyblue;
  }

  .right {
    	width: 200px;
      height: 100px;
    	background: orange;
  }

  .center {
    	flex: 1;
      height: 100px;
    	background: red;
  }
  ```

+ 圣杯布局

+ 双飞翼布局