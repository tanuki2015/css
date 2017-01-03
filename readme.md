# css设计指南笔记
## 5.2固定三栏布局
1. 首先需要<wrapper>,固定宽度960px，居中。
2. <header>无需浮动，自动摆在第一行。
3. <nav>，<article>,<aside>依次float:left.
4. <footer>引用clear:both后自动摆在最下。

### 三栏布局的问题
内容的增加或每栏margin,padding的增加，导致空间不够，把后面的<aside>挤到下面。

解决方法是：
1. 仔细调整每一栏的宽度（太麻烦，弃用）。
2. 为每一栏增加一个<inner>的容器，不设置宽度，在它上面设置padding和margin，不要动外面有宽度的div。
3. 最为简单的方法，给浮动的<nav>，<article>,<aside>应用box-sizing:border-box.

#### ie6,7不支持box-sizing时，应用borderBoxModel.js这个腻子脚本。

#### 预防过大的元素，img或文本。
可以给img使用{max-width:100%;},以限制图片不超过父元素的宽度。

## 5.3 三栏-中栏流动布局
1. 用负的外边距实现（麻烦，略过）。
2. 用css3单元格实现（ie7以下不支持，也没有腻子脚本）。

实现比较简单，给<nav>，<article>,<aside>加上`display:table-cell`就行了。

## 下拉菜单案例
分三步走完成整个案例。
### 第一步 所需信息如下：
1. button样式信息
  * 背景色：#eee;
  * 字体：1em helvetica, arial, sans-serif;
  * 字体颜色：#555;
  * 文字留白距离：.2em 1em;
  * 分割线宽度：3px;
  * 悬停时文本和背景颜色：#fff #aaa;
  * 点击时文本和背景颜色：#ccc #fff;
2. 功能样式：
  * ul要包围li
  * 水平排列菜单
  * 去掉默认列表符号
  * 为子菜单提供定位上下文（预留）
  * 让a充满列表项
  * 利用边框视觉上给button添加间隔效果
  * 去掉a的下划线
  * 临时隐藏子菜单

### 第二步 二级菜单
1. 视觉样式
  * 二级菜单宽度：9em
  * 二级菜单去掉右边框并添加上边框
2. 功能样式
  * 临时显示二级菜单
  * 相对于父菜单定位
  * list回复堆叠排列
  * 继续隐藏3级菜单
3 给二级菜单增加功能
  * 隐藏二级菜单
  * 鼠标hover到父元素时，显示二级菜单

### 第三步 三级菜单
  * 把三级菜单从父元素的下面定位到右边

### 第四步 完善功能，添加顶级菜单纵向显示选项
  * 添加vertical类
  * 设顶级nav容器宽度：8em
  * 去掉菜单右边的视觉间隔，换成上边
  * 顶层菜单垂直显示
  * 子菜单对齐
  * 突出显示选择路径

## form案例
直接修改两个form案例会节省时间。

## 搜索表单
见searchForm.html

## 弹出层

### css三角形

# 其他的知识点
1. 块元素会生成一个“块匡”， 而且在块框的前后加上“分隔符”
2. 不能继承的属性基本是“框模型”的属性：padding margin border background...

##  css权威指南
### chapter basic visual formatting

1. 每个element 都生成一个 element box
2. 每个element 都包含一个 content area
3. content area 周围是 padding, border, margin
4. padding, border, margin 可有，可无

1. 每个element都被最近的祖先盒子所包围和影响
2. 三种祖先盒子
  * block-level
  * inline-block
  * table-cell

#### block-level 的 horizontal formatting
1. 有宽度的box，增加padding, margin, border会增加element box 的width，占据更大空间。
2. content area 的宽度不变。

<p style="width: 200px;">wideness?</p>
<p style="width: 200px; padding: 10px;">wideness?</p>

3. 正常流中element box的宽度=父box
margin-left + border-left + padding-left + content area width + padding-right + border-right + margin-right = 父box的 width

4. 可使用的auto值是margin-left, margin-right和content area width。

5. auto值有一个的时候，这个值会设置为一个定值，使得上面规则3被满足。

6. auto值是两个margin时，则他们相等，内容自然居中。

7. text-align只能让块元素中的内联内容居中，而不是块元素居中（这句没看懂，反正img不行。）。

8. 如果3个都是auto，则margin被设置为0.
