# taobao淘宝购物车
###demo仅供学习参考！


### 在pc端实现的淘宝购物车页面实现了以下功能，或者说的高端一些，实现了一些与用户交互方面的功能。

　　1：顶部实现了hover状态和非ho隐藏，并且弹出的二级菜单absolute化。这里的icon涉及了css3中的伪元素。并且向下的按钮是使用css3实现的。

　　2：搜索框实现了功能比较多。
  
       搜索框的使用：输入lan，n按回车或者按搜索按钮；弹出的下拉框选择第三个产品，回车或按搜索按钮。
　　　　首先是当你输入某个字符串之后会有相应的下拉菜单弹出。这里涉及了jquery ajax 的方法，使用$.get方法去获取json数据，然后动态加载html，最后返回到客户端上。另外涉及了jquery中的键盘事件keyup，当keycode为13（也就是enter键）时，会有相应的json数据被异步加载，然后放到相应的容器内。这样做的好处是不用整页刷新，对客户体验较好，特别是在移动端上。异步加载会极大减少流量的消耗。

　　　　当然这里还要重点在说的是，如果希望可以操作异步加载的数据，然后返回到客户端上的相应内容时，这里需要用到事件代理和事件冒泡的原理。什么意思呢？就是说，如果你把一些事件绑定在被动态加载html的元素上面，那么这些被绑定的事件会失效。解决方法是需要将事件绑定到body（或者其他非动态加载的html）元素上。详细的我会在之后的文章中谈及。

　　3：商品的选择，查询，删除，增加。

　　　　选择商品大概有几种逻辑：当点击全选按钮时，全部商品被选择，并且计算相应的价格和商品数量；取消全选时，全部商品被取消，并且商品价格和数量相应变化；当在全选状态下，某个商品被取消选择，则取消全选状态，并且会相应计算商品价格和商品数量；当所有商品被全部选中时，全选按钮重新被激活，并且计算相应的商品价格和商品数量。

　　　　查询商品：如果想要查询自己购物车的商品，我的实现是自己去写一些json数据，然后通过ajax动态加载html，然后返回到客户端。

　　　　删除商品：pc端页面还有一个没有实现的就是当我去删除某个商品时，如何删除json数据里面的相应商品数据。我能做到的就是在页面上删除。做法是使用了jquery的detach()方法，而不是remove()方法。如果有博友知道怎么实现json数据内的相应商品数据一并删除，希望能给我留言，给予我一定的解决方案。

 　　4：固定底部的商品操作栏。

　　　　这里主要有两个知识点：一是让整个footer的父容器fixed，然后bottom设置为0。二是在.container元素上设置margin-bottom值，距离可视窗口底部有一定的距离。如果不设置的话，当拉到最后一个商品时，最后一个商品会被fixed的容器覆盖。用户体验不够好。
    
    
### 在移动端，一套代码实现了不同设备的响应式布局，我使用的media query最大支持1024px。因为我是第一次接触移动端页面，移动端淘宝购物车页面是基于css3的flexbox伸缩布局盒模型实现的，如果有什么不足之处，希望前端牛人指出，抱着学习的态度，本人积极改正。

    在移动端上，实现的功能相对简单，因为手机屏幕小的原因，对很多在pc端存在的元素，在移动端页面上都进行了相应地做了减法。
