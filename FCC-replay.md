# 应用视觉设计

- strong 加粗

- u 下划线

- em标签 斜体 用于强调文本

- s标签 删除线

- hr标签 水平线

- rgba设置颜色  a:alpha  透明度

- font-size 字体大小

- box-shadow

- opacity,设置透明度，1为完全不透明 0为完全透明

- text-transform:改变文本的大小写

- font-weight:设置字体粗细

- line-height，设置行间间距

- hover与伪类，伪类是添加到选择器上的选择器，用于选择特定状态的元素

- position:relative

- position:absolute,绝对定位的元素定位参照于最近的祖先元素，脱离文档流，若父元素没有添加定位元素(默认为relative)，则它会继续寻找直到body标签为止。

- position:fixed,相对浏览器窗口定位，特殊的绝对定位，脱离文档流，与绝对定位区别是不会随着屏幕滚动而移动(小广告专用定位方式！可恶！)

- float，脱离文档流，可设置其值为left或right，通常需要设置width属性来指定浮动元素占据的水平空间

- z-index:指定元素堆叠次序

- 元素居中方法一:margin:auto

- hsl(色相，饱和度，亮度)，CSS3引入此方式作为颜色的描述方式，如红色hsl(0,100%,50%)

- 颜色渐变:background: linear-gradient(gradient_direction, color 1, color 2, color 3, ...);

  -  background: linear-gradient(35deg, #CCFFFF, #FFCCCC);

     }

- 通过background:url()可以给页面添加纹理。

- transform:scale(2)，把元素放大两倍

- transform有很多用处，可以调整大小、移动、翻转、旋转。

- transform:skewX(-32deg),使元素沿着x轴倾斜-32度。skewY(24deg),使元素沿着y轴倾斜24度

- ::before,所选元素的第一个子元素，::after,所选元素的最后一个子元素，它们都必须配合content使用，当使用此属性实现形状时，把content的值设置为空字符串即可。

- animation属性控制动画外观，@keyframes控制动画各阶段的变化，animation-name设置动画名称，animation-duration设置动画花费时间。

  - ```css
      #rect {
     animation-name:rainbow;
     animation-duration:4s;
      }
      @keyframes rainbow{
        0%{
          background-color:blue;
        }
        50%{
          background-color:green;
        }
        100%{
          background-color:yellow;
        }
      }
    ```

- animation-fill-mode: forwards;    用于保持动画始终停留在最后一刻。

- animation-iteration-count: 3;  动画循环次数为3。infintie则动画无限循环

- animation-timing-function用来定义动画的速度曲线，如果要描述的动画是一辆车在指定时间内（animation-duration）从 A 运动到 B，那么 animation-timing-function 表述的就是车在运动中的加速和减速等过程。ease(默认值):低速开始，加速，结束前变慢。ease-out:高速开始、低俗结束 ease-in:低速开始，高速结束。linear:动画从头到尾速度相同。

- 贝塞尔曲线(Bezier curves):用于更细致地控制动画的速度曲线。cubic-bezier 函数包含了 1 * 1 网格里的4个点：p0、p1、p2、p3。 其中 p0 和 p3 是固定值，代表曲线的起始点和结束点，坐标值依次为 (0, 0) 和 (1, 1)。 你只需设置另外两点的 x 值和 y 值，设置的这两点确定了曲线的形状从而确定了动画的速度曲线。 在 CSS 里面通过 (x1, y1, x2, y2) 来确定 p1 和 p2。 以下就是 CSS 贝塞尔曲线的例子：

  - animation-timing-function: cubic-bezier(0.25, 0.25, 0.75, 0.75); 此时曲线是一条从原点到(1,1)的直线，即元素速度为线性，效果与linear相同，元素匀速运动。

# 应用无障碍

- alt='',img标签属性，用于当图片无法显示时替代图片，也有利于搜索引擎搜索 对于有标题的图片，依然需要添加 `alt` 文本，因为这样有助于搜索引擎记录图片内容

- `main` 标签用于呈现网页的主体内容，且每个页面应只有一个。`main` 标签也有一个内嵌的特性，以便辅助技术快速定位到页面的主体。 如果你在页面顶部看到过“跳转到主要内容”链接，那么使用 `main` 标签会自动让辅助设备具有这个跳转的功能

- article标签用于独立且完整的内容，section用于对与主题相关的内容进行分组。

- header标签可以为父级标签呈现简介信息或者导航链接，适用于那些在多个页面顶部重复出现的内容。`header` 的语义化特性也可以让辅助工具快速定位到它的内容

- nav标签用于使屏幕阅读器快速识别出页面的导航信息，它呈现页面中的主导航链接。

- footer类似nav，它位置页面底部，用于呈现版权信息或相关文档链接。

- audio，呈现音频内容，支持controls属性用于显示浏览器默认播放、停止和其他控制以及支持键盘功能。

  ```css
      <p>A sound clip of Zersiax's screen reader in action.
      <audio controls>
        <source src='https://s3.amazonaws.com/freecodecamp/screen-reader.mp3' type='audio/mpeg'>
        </source></audio>
      </p>
  ```

- figure与figcaption标签，用于展示可视化信息如图片、图表及其标题

- `label` 标签的文本内容通常会是表单组件的名称或标签。 这些文本表明了组件的意义，也提升了表单的可访问性。 `label` 标签的 `for` 属性将标签与表单组件绑定；同时，屏幕阅读器也会读取 `for` 属性的属性值。`for` 的属性值必须与表单组件的 `id` 属性值相同。

- `fieldset` 标签包裹整组单选按钮，实现这个功能。 它经常使用 `legend` 标签来提供分组的描述，以便屏幕阅读器用户会阅读 `fieldset` 元素中的每个选项。当选项的含义很明确时，如“性别选择”，`fieldset` 与 `legend` 标签可以省略。 这时，使用包含 `for` 属性的 `label` 标签就足够了

  - ```js
    <form>
      <fieldset>
        <legend>Choose one of these three items:</legend>
        <input id="one" type="radio" name="items" value="one">
        <label for="one">Choice One</label><br>
        <input id="two" type="radio" name="items" value="two">
        <label for="two">Choice Two</label><br>
        <input id="three" type="radio" name="items" value="three">
        <label for="three">Choice Three</label>
      </fieldset>
    </form>
    ```

- HTML5 规范添加了 `date` 类型来创建日期选择器。 如果浏览器支持，在点击 `input` 标签时，日期选择器会显示出来，这让用户填写表单变得更加容易。对于较老的浏览器，类型将默认为 `text`， 这样它可以通过 `label` 或 `placeholder` 文本向用户显示预期的日期格式

- 如果我们想在页面中添加一些只对屏幕阅读器可见的内容，可以用 CSS 来实现。 当信息为视觉格式（例如图表）时，但屏幕阅读器用户需要备用文稿（例如表格）来访问数据，在这种情况下， 使用 CSS 将屏幕的只读元素放到浏览器窗口可视区域之外

- HTML 提供 `accesskey` 属性，用于指定激活元素或者使元素获得焦点的快捷键。 添加 `accesskey` 属性可以让使用键盘的用户更高效率地导航。HTML5 允许在任何标签上使用这个属性。 该属性尤其适用于链接、按钮、表单组件等元素.

  - ```
    <button accesskey="b">Important Button</button>
    ```

- HTML 的 `tabindex` 属性有三种与标签焦点相关的功能。 当它在一个元素上时，表示该元素可以获得焦点。 tabindex 的值（可以是零、负整数或正整数）定义了行为。当用户使用键盘浏览页面时，诸如链接、表单控件等元素可以自动获得焦点。 它们获得焦点的顺序与它们出现在 HTML 文档流中的顺序一致。 我们可以通过将其他标签（如 `div`、`span`、`p` 等）的 `tabindex` 属性值设为 0 来让它们实现类似的效果。 比如

  - ```js
    <div tabindex="0">I need keyboard focus!</div>
    ```

  - 使用 `tabindex` 属性还可以让 CSS 伪类 `:focus` 在 `p` 标签上生效

  - `tabindex` 属性还可以指定元素的 tab 键焦点顺序， 将它的值设置为大于等于 1 的整数，就可以实现这个功能

- 媒体查询是 CSS3 中引入的一项新技术，它可以根据不同的视口大小调整内容的布局。 视口是指浏览器中，用户可见的网页内容。 视口会随访问网站的设备不同而改变.媒体查询由媒体类型组成，如果媒体类型与展示网页的设备类型匹配，则应用对应的样式。 你可以在媒体查询中使用各种选择器和样式.eg:

  - ```js
    //标准格式:
    @media (max-width: 100px) { /* CSS Rules */ }
    @media (min-height: 350px) { /* CSS Rules */ }
    //当设备的高度小于等于 800px 时，p 标签的 font-size 为 10px
    @media (max-height: 800px) {p{
      font-size:10px;
    }}  
    ```

- 使用css使图片自适应:设置 `max-width` 值为 `100%` 可确保图片不超出父容器的范围；设置 `height` 属性为 `auto` 可以保持图片的原始宽高比

- 让图像正确出现在高分辨率显示器（例如 MacBook Pros “Revistina display”）上的最简单方式， 是定义它们的 `width` 和 `height` 值为原始值的一半

- 除了使用 `em` 或 `px` 设置文本大小，你还可以用视窗单位来做响应式排版。 视窗单位和百分比都是相对单位，但它们是基于不同的参照物。 视窗单位是相对于设备的视窗尺寸（宽度或高度），百分比是相对于父级元素的大小。四个不同的视窗单位分别是：

  - `vw`：如 `10vw` 的意思是视窗宽度的 10%。
  - `vh：` 如 `3vh` 的意思是视窗高度的 3%。
  - `vmin：` 如 `70vmin` 的意思是视窗的高度和宽度中较小一个的 70%。
  - `vmax：` 如 `100vmax` 的意思是视窗的高度和宽度中较大一个的 100%

# CSS弹性盒子

- display:flex
- 给元素添加 `display: flex` 属性可以让它变成 flex 容器， 然后可以让元素的项目排列成行或列。 只要给父元素添加 `flex-direction` 属性，并把属性值设置为 row(默认值) 或 column，即可横向排列或纵向排列它的所有子元素。 创建一行将使子项水平对齐，创建一列将使子项垂直对齐。`flex-direction` 的其他可选值还有 `row-reverse` 和 `column-reverse`
- flex 子元素有时不能充满整个 flex 容器， 所以我们经常需要告诉 CSS 以什么方式排列 flex 子元素，以及调整它们的间距。 可以通过 `justify-content` 属性的不同值来实现。
  - 如果把 flex 容器设为一个行，它的子元素会从左到右逐个排列； 如果把 flex 容器设为一个列，它的子元素会从上到下逐个排列。 子元素排列的方向被称为 **main axis（主轴）**。 对于行，主轴水平贯穿每一个项目； 对于列，主轴垂直贯穿每一个项目。
  - 对于如何沿主轴线排放 flex 项目，有几种选择。 很常用的一种是 `justify-content: center;`：即 flex 子元素在 flex 容器中居中排列。 其他选择包括：
    - `flex-start`：从 flex 容器的起始位置开始排列项目。 对行来说是把项目移至左边， 对于列是把项目移至顶部。 如未设置 `justify-content` 的值，那么这就是默认值。
    - `flex-end`：从 flex 容器的终止位置开始排列项目。 对行来说是把项目移至右边， 对于列是把项目移至底部。
    - `space-between`：项目间保留一定间距地沿主轴居中排列。 第一个和最后一个项目被放置在容器边沿。 例如，在行中第一个项目会紧贴着容器左边，最后一个项目会紧贴着容器右边，然后其他项目均匀排布。
    - `space-around`：与`space-between`相似，但头尾两个项目不会紧贴容器边缘，所有项目之间的空间均匀排布。
    - `space-evenly`：头尾两个项目不会紧贴容器边缘，所有项目之间的空间均匀排布
- Flex 容器中，与主轴垂直的叫做 **cross axis（交叉轴）**。 行的交叉轴是垂直的，列的交叉轴是水平的。CSS 中的 `align-items` 属性用来定义 flex 子元素沿交叉轴的对齐方式。`align-items` 的可选值包括：
  - `flex-start`：从 flex 容器的起始位置开始对齐项目。 对行来说，把项目移至容器顶部； 对列来说，是把项目移至容器左边。
  - `flex-end`：从 flex 容器的终止位置开始对齐项目。 对行来说，把项目移至容器底部； 对列来说，把项目移至容器右边。
  - `center`：把项目居中放置。 对行来说，垂直居中（项目距离顶部和底部的距离相等）； 对列来说，水平居中（项目距离左边和右边的距离相等）。
  - `stretch`：拉伸项目，填满 flex 容器。 例如，排成行的项目从容器顶部拉伸到底部。 如未设置`align-items`的值，那么这就是默认值。
  - `baseline`：沿基线对齐。 基线是文本相关的概念，可以认为它是字母排列的下端基准线。
- CSS flexbox 有一个把 flex 子元素拆分为多行（或多列）的特性。 默认情况下，flex 容器会调整项目大小，把它们都塞到一起。 对于行来说，所有项目都会在一条直线上。使用 `flex-wrap` 属性可以使项目换行展示。 这意味着多出来的子元素会被移到新的行或列。 换行发生的断点由子元素和容器的大小决定。换行方向可选值为:
  - `nowrap`：默认值，不换行。
  - `wrap`：如果排列以行为基准，就将行从上往下排列；如果排列以列为基准，就将列从左往右排列。
  - `wrap-reverse`：如果排列以行为基准，就将行从下往上排列；如果排列以列为基准，就将列从右往左排列
-  `flex-shrink` 属性。 使用之后，如果 flex 容器太小，则子元素会自动缩小。 当容器的宽度小于里面所有子元素的宽度之和时，所有子元素都会自动压缩。子元素的 `flex-shrink` 接受数值作为属性值。 数值越大，则该元素与其他元素相比会被压缩得更厉害。 比如，一个项目的 `flex-shrink` 属性值为 `1`，另一个项目的 `flex-shrink` 属性值为 `3`，那么后者相比前者会受到 `3` 倍压缩
- flex-grow属性，与flex-shrink相反。
- `flex-basis` 属性定义了在使用 CSS 的 `flex-shrink` 或 `flex-grow` 属性对元素进行调整前，元素的初始大小.单位与其他表示尺寸的属性的单位一致（`px`、`em`、`%` 等）。 如果值为 `auto`，则项目的尺寸随内容调整
- flex: 1 0 10px; 会把项目属性设为 flex-grow: 1;、flex-shrink: 0; 以及 flex-basis: 10px;   属性默认值为flex: 0 1 auto;
- `order` 属性告诉 CSS flex 容器里子元素的顺序。 默认情况下，项目排列顺序与源 HTML 文件中顺序相同。 这个属性接受数字作为参数，可以使用负数
- flex 子项目的最后一个属性是 `align-self`。 这个属性允许你调整单个子元素自己的对齐方式，而不会影响到全部子元素。 因为 `float`、`clear` 和 `vertical-align` 等调整对齐方式的属性都不能应用于 flex 子元素，所以这个属性显得十分有用。`align-self` 可设置的值与 `align-items` 的一样，并且它会覆盖 `align-items` 所设置的值

# CSS网格

- display:grid    css网格中，父元素称为容器container,子元素称为项items

- 在一个网格容器中使用 `grid-template-columns` 属性可以添加一些列，示例如下：

  - grid-template-columns:100px 100px 100px;
  - `grid-template-columns` 属性值的个数表示网格的列数，每个值表示相应的列宽度
  - grid-template-rows,设置行数

- 在 CSS 网格中，可以使用绝对单位（如 `px`）或相对单位（如 `em`）来定义行或列的大小。 下面的单位也可以使用：

  - `fr`：设置列或行占剩余空间的比例，

    `auto`：设置列宽或行高自动等于它的内容的宽度或高度，

    `%`：将列或行调整为它的容器宽度或高度的百分比

  - grid-template-columns: auto 50px 10% 2fr 1fr;    第一列的宽与它的内容宽度相等；第二列宽 50px；第三列宽是它容器的 10%；最后两列，将剩余的宽度平均分成三份，第四列占两份，第五列占一份。

- grid-column-gap，设置列之间的间距，grid-row-gap，设置行间距，grid-gap，第一个值为行间距，第二个值为列间距。

- grid-column用于设置一个网格项占据几列，网格中假想的水平线和垂直线被称为线（lines）。 这些线在网格的左上角从 1 开始编号，垂直线向右、水平线向下累加计数。grid-column: 1 / 3表示网格项从左侧第一条线开始到第三条线结束，占用两列。

- grid-row,设置占据行数

- 在 CSS 网格中，每个网格项的内容分别位于被称为单元格（cell）的框内。 你可以使用网格项的 `justify-self` 属性，设置其内容的位置在单元格内沿水平轴的对齐方式。 默认情况下，这个属性的值是 `stretch`，这将使内容占满整个单元格的宽度。 该 CSS 网格属性也可以使用其他的值：

  - `start`：使内容在单元格左侧对齐。

    `center`：使内容在单元格居中对齐。

    `end`：使内容在单元格右侧对齐。

  - align-self，设置沿竖直方向对齐方式。‘

- justify-items，设置网格中所有网格项水平方向对齐方式。align-items，设置网格中所有网格项垂直方向对齐方式

- grid-template-areas 可以将网格中的一些单元格组合成一个区域

  - ```js
    grid-template-areas:
      "header header header"
      "advert content content"
      "advert footer footer";
    //上面的代码将网格单元格分成四个区域：header、advert、content 和 footer。 每个单词代表一个单元格，每对引号代表一行js
    ```

  - 在为网格添加区域模板后，可以通过引用你所定义的区域的名称，将元素放入相应的区域。 为此，你需要对网格项使用 `grid-area`

    - ```js
      .item1 {
        grid-area: header;
      }
      //此时class 为 item1 的网格项就被放到了 header 区域里
      ```

  - 如果网格中没有定义区域模板，你也可以像这样为它添加一个模板。

    - ```js
      item1 { grid-area: 1/1/2/4; } //网格项将占用第 1 条水平网格线（起始）和第 2 条水平网格线（终止）之间的行，及第 1 条垂直网格线（起始）和第 4 条垂直网格线（终止）之间的列。
      ```

- repeat 函数减少重复,eg:  grid-template-rows: repeat(100, 50px);

- `minmax` 也可用于设置 `grid-template-columns` 和 `grid-template-rows` 的值。 它的作用是在网格容器改变大小时限制网格项的大小。 为此，你需要指定网格项允许的尺寸范围。eg:

  - grid-template-columns: 100px minmax(50px, 200px);     第一列宽度为 100px，第二列宽度最小值是 50px，最大值是 200px

- auto-fill,自动填充功能， 它的功能是根据容器的大小，尽可能多地放入指定大小的行或列。 你可以通过结合 `auto-fill` 和 `minmax` 来更灵活地布局

- `auto-fit` 效果几乎和 `auto-fill` 一样。 不同点仅在于，当容器的大小大于各网格项之和时，`auto-fill` 会持续地在一端放入空行或空列，这样就会使所有网格项挤到另一边；而 `auto-fit` 则不会在一端放入空行或空列，而是会将所有网格项拉伸至合适的大小

- 将元素转换为网格只会影响其子元素（即直接后代元素，英文为 direct descendants。意思是一个元素的所有后代元素中，父级元素为该元素的所有元素）。 因此，如果我们把某个子元素设置为网格，就会得到一个嵌套的网格





