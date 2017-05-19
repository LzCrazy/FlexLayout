### FlexLayout
#### flex布局
- display:flex;将对象作为弹性伸缩盒展示，用于块级元素
- display:inline-flex;将对象作为弹性伸缩盒展示，用于行内元素

#### flex作用于Box容器上的6个属性
1.flex-direction

用于指定Flex主轴的方向，继而决定Flex子项在Flex容器中的位置
取值：row|row-reverse|column|column-reverse
- row:默认值，水平主轴方向从左到右
- row-reverse:与row相反
- column:垂直主轴方法从上到下
- column-reverse:与column相反

[demo演示](/flexLayout.html)

2.flex-wrap

用于指定Flex子项是否换行。
取值：nowrap|wrap|wrap-reverse
- nowrap:默认值，表示不换行，Flex子项可能溢出
- wrap:换行，溢出的子项将放到下一行
- wrap-reverse:反方向换行

[demo演示](/flexLayout1.html)

3.flex-row

复合属性，是flex-directive和flex-wrap的简写属性，指定Flex子项排列方式

4.justify-content

用于指定水平主轴方向上的Flex子项的对齐方式。
取值：flex-start|flex-end|center|space-between|space-around
- flex-start：默认值，表示与行的起始位置对齐
- flex-end：表示与行的结束位置对齐
- center：表示与行中间对齐
- space-between：表示两端对齐，中间间距相等。特殊情况，当剩余空间为负数或者只有一个项时，效果如flex-start
- space-around：表示间距相等，中间间距是两端的两倍，当剩余空间为负数或只有一项，效果如center

[demo演示](/flaxLayout2.html)

5.align-items

用于指定水质侧轴方向上flex子项的对齐方式
取值：stretch|flex-start|flex-end|baseline
- stretch:默认值，当Flex子项没有设置高度或高度为auto时，stretch起作用，将Flex子项高度设置为行高度
。在只有一行的情况下，行的高度为容器的高度
- flex-start：测轴开始位置对齐
- flex-end：侧轴结束位置对齐
- center：侧轴中间对齐
- baseline：基线对齐，当行内轴与侧轴同一线上，即所有Flex子项的基线在同一线上，效果如flex-start
[demo演示](/flexLayout3.html)

6.align-content

只作用在多行的情况下，用于多行对齐方法
取值：stretch|flex-start|flex-end|center|space-between|space-around
- stretch：默认值，当Flex子项未设置高度或者高度值为auto时，stretch起作用，将Flex子项高度设置为行高度。
- flex-start：表示各行与侧轴开始位置对齐，第一行紧靠侧轴开始边界，之后的每一行都紧靠前面一行
- flex-end：表示各行与侧轴的结束位置对齐，最后一行紧靠侧轴结束边界，之后的每一行都紧靠前面一行
- center：表示各行与侧轴中间对其
- space-between：表示两端对齐，中间间距相等。要注意特殊情况，当剩余空间为负数时，效果等同于flex-start
- space-around：表示各行之间间距相等，中间间距是两端间距的2倍。要注意特殊情况，当剩余空间为负数时，效果等同于center
[demo](/flexLayout3.html)
再次强调：该属性只作用于多行的情况，在只有一行的Flex容器上无效，另外该属性可以很好的处理，换行以后相邻行之间产生的间距。

#### Flex作用于子项上的6个属性
1.order

该属性用于指定Flex子项的排列顺序，数值越小，越靠前，可以为负数
- 取值：数字，默认值为：0

[demo](/flexLayout4.html)


2.flex-grow

用来指定Flex子项的扩展比例，不可为负数，Flex容器会根据Flex子项设置的比例作为比率来分配空间
- 取值：数字，默认值：0，表示即使有剩余空间，Flex子项也不会扩展

3.flex-shrink

Flex子项的收缩比例，不可为负数，Flex容器会根据Flex子项设置的收缩比例作为比率来收缩各个Flex子项
- 取值：数值，默认值为1，表示所有子项在剩余空间为负数时，等比例收缩
- 注意：flex-shrink只能在不换行的情况下使用

4.flex-basis

用来指定Flex子项的占据的空间，不可以为负数
取值：auto | length | percentage | content
- auto：默认值，计算规则：检索Flex子项是否设置了width值（或者height值，取决于flex-direction），如果设置了非auto的值，则使用width值（或者height值），若没有则使用content
- length：用长度值定义宽度，不可为负数
- percentage：使用百分比定义宽度，不可为负数
- 注意：
1.设置flex-grow进行分配剩余空间，或者使用flex-shrink进行收缩都是在flex-basis的基础上进行的；
2.当flex-basis的值以及width（或者height）的值均为非auto时，
     1）若content长度同时大于flex-basis的值以及width（或者height）的值，此时以flex-basis与width（或者height）中值大的为准 ，但是，如果子项设置了overflow: hidden;或者overflow: auto;，此时以flex-basis值为准；
     2）若content长度同时小于flex-basis的值以及width（或者height）的值，此时以flex-basis值为准；
     3）若content长度小于flex-basis的值，大于width（或者height）的值，此时以flex-basis值为准；
     4）若content长度大于flex-basis的值，小于width（或者height）的值，此时以content自身长度值为准；
3.当width（或者height）的值为auto时，且内容的长度大于flex-basis设置的值，此时以content自身长度值为准，且不能进行flex-shrink收缩。相反如果内容的长度小于flex-basis设置的值，则会使用flex-basis设置的值；
4.当存在最小值 min-width（min-height）时，且 flex-basis的值小于最小值时，宽度以最小值为准，当 flex-basis的值大于最小值时，以 flex-basis的值为准

5.flex

复合属性，是flex-grow 、 flex-shrink 和 flex-basis 的简写属性，用来指定Flex子项如何分配空间
取值：none | 各拆分项属性
- none：0 0 auto
- auto：1 1 auto
- 1：1 1 0%
- 0 auto 或 initial：0 1 auto 即初始值

6.align-self

用来单独指定某Flex子项的对齐方式
取值：auto | flex-start | flex-end | center | baseline | stretch
- auto：默认值，查找父元素的align-items值，如果没有则取值为stretch
- 其他值同align-items

##### 如果想要详细了解Demo，可以查看[FexLayout布局Demo](https://github.com/LzCrazy/FlexLayout)