# 1.CSS总结

## CSS术语

- 属性:如height、width等
- 关键字:如transparent、solid、inherit等，其中inherit称为泛关键字，即所有CSS属性都可以使用的属性
- 变量:CSS中变量较少，如CSS3中的currentColor就是变量。
- 长度单位:CSS中的单位有时间单位(s、ms)，角度单位(deg、rad)，但最常用的是长度单位(px,em等)，注意2%是一个值，%不是长度单位！长度单位分为两种:
  - 相对长度单位:
    - 相对字体长度单位,如em和ex,还有CSS3的rem和ch
    - 相对视区长度单位:如vh、vw、vmin和vmax
  - 绝对长度单位:px
- 功能符:值以函数形式指定，主要用于表示颜色(rgba和hsla)、背景图片地址url、元素属性值、计算calc和过渡效果等。
- 属性值:属性冒号后的所有内容，如z-index:1的1
- 声明块:由花括号包裹的一系列声明,如{height:50px;}
- 规则和规则集:出现了选择器且后面跟着声明块，如.tao{height:50px;}
- 选择器，用来瞄准目标元素的东西
  - 类选择器:指以点号.开头的选择器，元素们可以应用同一个类选择器
  - ID选择器:井号#开头，ID一般指向唯一元素，但若出现在多个元素上时会雨露均沾，不建议这么使用
  - 属性选择器:含有[]的选择器，如[title = 'css-world']{}
  - 伪类选择器，指前面有个英文冒号的选择器，如:first-child
  - 伪元素选择器,指有两个连续冒号的选择器，如::first-line
- 关系选择器:根据与其他元素的关系选择元素的选择器，常见符号有空格，>,~,+
  - 后代选择器:选择所有合乎规则的后代元素，空格连接
  - 相邻后代选择器:仅选择合乎规则的儿子元素，又叫子选择器，>连接
  - 兄弟选择器，选择当前元素后面的所有合乎规则的兄弟元素，~连接
  - 相邻兄弟选择器，仅选择当前元素相邻的那个合乎规则的兄弟元素，+连接
- @规则，指以@字符开始的一些规则，如@media,@font-face,@page,@support等

### CSS中的未定义行为:

指规范描述以外的场景，如不同浏览器对同一代码的表现效果不同，因为不同浏览器的规范不同。

# 随笔

- ul，li里的字自带原点，需要用list-style: none;去掉    且每个li都会自动换行，可用float:left使其在一行中显示
- 超链接文本自带下划线，可用text-decoration:none去掉
- ![image-20211113152304578](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211113152304578.png)

![image-20211113154052208](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211113154052208.png)![image-20211113154810156](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211113154810156.png)

- padding也有背景颜色，与content相同
- width为内容宽度，但width不等于真实占有宽度 真实宽度 = width+padding+border

# 浮动

#### 标准文档流

- 底边对齐，高矮不齐
- 空白折叠
- 块级元素与行内元素
  - 块级:霸占一行、能接受设置宽高，默认为父亲的100%
  - 行级:与其他元素并排，不能设置宽高，默认为文字的宽度
- ![image-20211114095358405](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211114095358405.png)

- 脱离文档流的三种办法:浮动、绝对定位、固定定位
- 浮动的四个性质:
  - 浮动的元素脱标，不区分块级、行内
  - 浮动的元素相互贴靠
  - 浮动的元素有字围效果
  - 收缩:浮动元素若没有设置width，则自动收缩为内容的宽度(类似行内元素)
- 浮动原则:永远不是一个东西单独浮动，浮动都是一起浮动，要浮动，大家都浮动

### 清除浮动

- 给浮动的祖先元素设置高度(必须大于儿子高度)
- clear:both,即不允许左右侧有浮动对象，它的问题是会导致margin属性失效
- 隔墙法:我们可以在这两个div中间用一个新的div隔开，然后给这个新的div设置`clear: both;`属性；同时，既然这个新的div无法设置margin属性，我们可以给它设置height，以达到margin的效果（曲线救国）。这便是隔墙法。
- ![image-20211114103951165](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211114103951165.png)
- 内墙法:在div里加一个div且设置clear both，此时box1高度可以自适应内容
- ![image-20211114104018105](http://r19kczb6x.hn-bkt.clouddn.com/img/image-20211114104018105.png)
- overflow:hidden (最常用的方法)一个父亲不能被自己浮动的儿子，撑出高度。但是，只要给父亲加上`overflow:hidden`; 那么，父亲就能被儿子撑出高了。这是一个偏方

​	

- 表达父子的距离，要用父亲的padding而不是儿子的margin

### 定位

- 相对定位:不脱标，只是影子飘出去
- 绝对定位:
  - 脱标，参考点:若是用top，则参考点为页面左上角(而不是浏览器左上角)，若用bottom，则参考点是浏览器首屏窗口尺寸！！！，对应页面左下角。
  - 若一个绝对定位的元素，其祖先元素已出现定位(无论哪种)，那么此元素以最近的已经定位的祖先元素为参考点
  - 绝对定位的儿子无视参考的那个盒子的padding
- z-index:谁盖住谁，不设置则谁在后谁优先级更高。

### CSS3选择器:

- 属性选择器，标志符号[],如`E[title="abc"]`选中页面的E元素，并且E需要带有title属性，且属性值**完全等于**abc。
- 结构伪类选择器,标志符号:,如E:first-child，E:last-child，E:nth-child(n)，E:first-of-type(匹配同类型中的第一个同级兄弟元素E),`E:nth-of-type(n)` (匹配同类型中的第n个同级兄弟元素E)。
- 伪元素选择器，标志符号:,如E::before，E::after，E::first-letter，E::first-line’

### CSS3盒子:

- 利用box-sizing属性，开发人员可以指定盒子高度和宽度的计算方式
- box-sizing: content-box(默认方式)，此时width和height是内容区域的宽高，盒子实际宽度 = width+padding+border，此时改变padding和border不改变内容宽高而是盒子总宽高变化。
- box-sizing: border-box:,此时width和height是盒子总宽高，盒子实际宽度 = width,此时改变padding和border会改变内容宽度，盒子总宽高不变。

### 边框圆角

- border-radius:60px 120px 水平半径 垂直半径

### css3中的flex

- 子元素们会在水平方向上，从左至右排列
- flex 布局的子元素不会脱离文档流
- flex-direction:设置子元素排列方向，默认为row，从左到右排列，还有row-reverse,column,column-reverse.
- flex-wrap:控制子元素溢出时的换行处理
- justify-content:控制子元素在主轴上的排列方式

### 常见的布局方法

1、table 表格布局：早期使用的布局，如今用得很少。
2、float 浮动 + margin：为了兼容低版本的IE浏览器，很多网站（比如腾讯新闻、网易新闻、淘宝等）都会采用 float 布局。
3、inline-block 布局：对外的表现是行内元素（不会独占一行），对内的表现是块级元素（可以设置宽高）。
4、flex 布局：为布局而生，非常灵活，是最为推荐的布局写法，唯一的缺点是兼容性问题

### margin

- 外边距margin用于控制元素的边框与其他元素的边框的距离

- 标准流中竖直方向的margin不叠加，取较大的值作为margin，水平方向可以叠加。
- 盒子居中margin:0,auto:即上下的margin为0，左右的margin都尽可能大，于是就居中了，只适用于标准流盒子，且盒子必须有width(没有明确width那么它的width就是霸占整行，无意义。)它的作用是使盒子居中而不是文本居中，文本居中使用text-align:center

### 水平垂直居中！

#### 1.如何让一个行内元素水平垂直居中

- 行内元素水平居中:text-align   
- 行内元素垂直居中:让文字行高等于盒子高度，比如.father{height:20px line-height:20px}

#### 2.如何让一个块级元素水平垂直居中

- 水平居中:margin:auto
- 垂直居中:
  - 方法一:绝对定位+translate:translate()函数使用百分比值时是以自身的宽度和高度为基准进行换算和移动的。 此时父元素需要设置定位(不设置的话子元素会以页面为参考)，然后子元素设置{top:50% left:50% transform:translate(-50%,-50%)}
  - 方法2:flex布局:将父容器设置为flex布局，给父容器加一个justify-content:center,这样子元素就能水平居中，再给父容器加个属性align-items:center,这样子元素就能垂直居中。弊端是父容器里所有元素都会垂直居中，无法指定某个元素居中
  - 方法3：flex布局+margin:auto,给父容器设置display:flex,给子元素设置margin:auto即可

### 伪类和伪元素的区别是什么

- 概念上的区别
  - 伪类表示一种状态
  - 伪元素是真的有元素。比如 ::after 是真的有元素，可以在页面上显示内容。
- 使用上的区别
  - 伪类：使用单冒号
  - 伪元素：使用双冒号



- #### 字体降级使用:

- ```css
  p {
    font-family: Helvetica, sans-serif;   //sans-serif为备用字体
  }
  ```

- 在body的CSS里设置color会使页面所有颜色都设置为color
- 行内式优先级高于ID选择器！！！
- 自定义CSS 变量：在前面加两个--,如--penguin-skin:  ,引用时需要用var括起来:background: var(--penguin-skin).自定义的CSS变量是可以继承的，所以它经常定义在:root{}里，这样可以被所有选择器继承。

