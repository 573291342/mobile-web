## 视口（viewport）

1. 就是浏览器显示内容的屏幕区域

   1. 布局视口(layout viewport)

      - 一般移动设备的浏览器都默认设置了一个布局视口，解决早期pc端页面在移动端显示的问题

        苹果安卓都会把这个视口分辨率设置为980px

   2. 视觉视口(visual viewport)

      - 用户正在看到的网站区域
      - 用户可以缩放操作视口，视口仍保持原来宽度

   3. 理想视口(ideal viewport)

      - 为使网站在移动端有最理想的浏览和阅读宽度而设定的
      - 需要手动添写meta视口标签

### meta视口标签

**标准写法**

```html
<meta name="viewport"
    content="width=device-width, user-scalable=no, minimum-scale=1.0, maxmimum-scale=1.0, initial-scale=1.0">
```


|      属性      |                          说明                          |
| :------------: | :----------------------------------------------------: |
|     width      | 宽度设置的是viewport宽度，可以设置device-width的特殊值 |
| initial-scale  |                初始缩放比，大于0的数字                 |
| maxmimum-scale |                最大缩放比，大于0的数字                 |
| minimum-scale  |                最小缩放比，大于0的数字                 |
| user-scalable  |            用户是否可以缩放，yes或no(1或0)             |

## 二倍图

### 物理像素&物理像素比

1. 物理像素就是分辨率（一行一列可以显示的像素点）
2. 开发时的1px不一定等于1物理像素 
3. 在pc端1px=1物理像素 
4. 视网膜屏幕技术

### 背景缩放

```css
   /* background-size: 图片宽度 图片高度 */
   /* background-size: 100px 100px */
   /* background-size: 图片宽度 高度等比例拉伸 */
   /* background-size: 100px  */
   /* 单位可以时% 相对于父盒子来说 */
   /* background-size: 50%  */
   /* 把图片宽高等比例拉伸到完全覆盖盒子 */
   /* background-size: cover; */
   /* 宽高等比例拉伸，直至宽度或者高度达到盒子宽度或高度 则不进行拉伸 */
   /* background-size: contain; */
```

## 移动端开发选择

1. ### 单独制作移动端页面（主流）

   **在域名前加m(mobile)**

   - 京东
   - 淘宝
   - 苏宁

2. ### 响应式页面兼容移动端（其次）

   制作麻烦，要考虑兼容性问题

   1. 三星官网

## 移动端技术解决方案

### 移动端浏览器

移动端基本以webkit内核为主

### css初始化 normalize.css

### css3盒子模型

```css
/* c3盒子模型 border 和 padding 不会撑大盒子*/
   box-sizing: border-box;
   width: 200px;
   height: 200px;
   background-color: skyblue;
   border: 5px solid #333;
   padding: 10px;
```

### 特殊样式

```css
/* css3盒子模型 */
   box-sizing: border-box;
   -webkit-box-sizing: border-box;
   /* 点击高亮 清除高亮 设置为transparent 完全透明 */
   -webkit-tap-highlight-color: transparent;
   /* 在移动端浏览器默认的外观在iOS上加上这个属性才能给按钮和输入框自定义样式 */
   -webkit-appearance: none;
  /* 禁用长按页面时的弹出菜单 */
  img,a {-webkit-touch-callout: none; }
```

## 移动端常见布局

### 移动端技术选型

1. ### 单独制作移动端页面（主流）

   - 流布局（百分比布局）
     - 最大宽度 max-width ,最小宽度 min-width
   - flex布局（推荐）
   - less+rem+媒体查询
   - 混合布局

2. ### 响应式页面兼容移动端（其次）

   - 媒体布局
   - bootstrap

## 案例

### 二倍精灵图

1. 先把精灵图缩放到原来的一半
2. 再测量距离
3. 最后在backgroung-size 缩小为原来的一半

## flex布局

### flex布局原理

- 当我们为父盒子设置为flex布局后，子元素的float、clear和vertical-align属性将失效
- 伸缩布局 = 弹性布局 = 伸缩盒布局 = 弹性布局 = flex布局

### 常见父项属性

- flex-direction: ;设置主轴的方向

  |     属性值     | 说明           |
  | :------------: | -------------- |
  |      row       | 默认值从左到右 |
  |  row-reverse   | 从右到左       |
  |     column     | 从上到下       |
  | column-reverse | 从下到上       |

- justify-content: ;设置主轴上的子元素排列方式

  |    属性值     | 说明                                      |
  | :-----------: | ----------------------------------------- |
  |  flex-start   | 默认从头部开始 如果主轴是x轴，则从左到右  |
  |   flex-end    | 从尾部开始排列                            |
  |    center     | 再主轴居中对齐（如果主轴是x轴则水平居中） |
  | space-around  | 平分剩余空间                              |
  | space-between | 先连边贴边，再平分剩余空间（重要）        |

- flex-wrap: ;设置子元素是否换行

  ```css
  .box{
    flex-wrap: nowrap | wrap | wrap-reverse;
  	/*nowrap（默认）：不换行。*/
      /*wrap：换行，第一行在上方。*/
     /* wrap-reverse：换行，第一行在下方。*/
  }
  ```

- align-content: ;设置侧轴上的子元素的排列方式 （多行）

  - flex-start：侧轴的起点对齐。
  - flex-end：侧轴的终点对齐。
  - center：侧轴的中点对齐。
  - space-between：侧轴 两端对齐，轴线之间的间隔平均分布。
  - space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
  - stretch（默认值）：轴线占满整个交叉轴。

- align-items: ;设置侧轴上的子元素排列方式（单行）

  - flex-start：侧轴从上到下。
  - flex-end：侧轴从下到上。
  - center：侧轴居中。
  - baseline: 项目的第一行文字的基线对齐。
  - stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

- flex-flow: ;复合属性，相当于同时设置了flex-direction 和 flex-wrap

### 常见子项属性

- flex子项目占的份数
- align-self控制子项自己在侧轴的排列方式  **给自己加属性不要给父亲加**
- order属性定义子项的排列顺序（前后顺序）**默认开头是0**

## 案例

## rem基础

rem 是一个相对单位，类似于em, em 是父元素字体大小，不同的是rem 是基准是相对于html元素的字体大小。如，根元素（html）设置font-size=12px;非根元素设置width:2rem;则换成px表示就是24px

rem优点可以通过修改html里面的文字大小来修改页面中的元素大小可以整体控制

## 媒体查询

- 使用@media查询，可以针对不同的媒体类型定义不同的样式
- @media可以针对不同的屏幕尺寸设置不同的样式
- 当你重启浏览器大小的过程中，页面也根据浏览器的宽高重新渲染页面
- 目前的苹果，安卓，平板设备都用到多媒体查询

### 语法规范

```css
@media mediatype and|only|not(media feature){
css-Code
}
```

- 用@media开头注意@符号

- mediatype 媒体类型

  |   值   | 说明                         |
  | :----: | ---------------------------- |
  |  all   | 用于所有设备                 |
  | print  | 用于打印机，打印预览         |
  | screen | 电脑屏幕，智能手机，平板电脑 |

- 关键字 and not noly

- media feature 媒体特性 必须有小括号包含

  | 值        | 说明                                 |
  | --------- | ------------------------------------ |
  | width     | 定义输出设备中页面可见区域的宽度     |
  | min-width | 定义输出设备中页面最小可见区域的宽度 |
  | max-width | 定义输出设备中页面最大可见区域的宽度 |

### 引入资源

当样式比较繁多的时候，我们可以针对不同的媒体使用不同的stylesheets样式表

语法规范：

```html
<link rel="stylesheet" href="mystylesheet.css" media="mediatype and|not|only (media feature)"> 
```

## less基础

- css代码没有逻辑，冗余度高
- css没有计算能力
- 不方便维护，不利于复用 

### less介绍 css预处理器

[官网less](http://lesscss.cn)

1. less变量

   @变量名：值；

   规范：

   - 必须以@为前缀
   - 不能包含特殊字符
   - 不能以数字开头
   - 大小写敏感

2. less编译

3. less嵌套

   - less嵌套 子元素样式直接写到父元素里面就可以
   - 如果没有&符号，则会被解析为后代选择器，如果有&符号，则会解析为自身或者父元素的伪类

4. less运算

   - 任何数字和颜色或者变量都可以参与运算
   - 运算符左右两边必须有空格
   -  如果只有一个数有单位则以结果就以这个单位为准
     1. 两个数都有单位，而且不一样，最后结果以第一个单位为准

## rem适配方案

### 方案1

1. 页面元素取值rem值：页面元素值px/（屏幕宽度/划分分数）
2. 屏幕款苏/划分分数 就是html font-size 的大小
3. 或者：页面元素的rem的值=页面元素值px/html font-size 字体大小

具体步骤：

1. 首先选一套标准尺寸 750px为准
2. 用屏幕尺寸 除以 划分的份数 得到了 html 里面的文字大小 但是我们知道不同屏幕尺寸的文字大小是不一样的
3. 页面元素的rem 值 = 页面元素在750像素下px值 / html 里面的文字大小