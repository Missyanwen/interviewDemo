<template>
	<div>
		<center>Vue只支持ie9及以上版本</center>
		<ul>
			<li><strong>什么是MVVM？</strong></li>
			<li>
				<b>MVVM：</b>由Model,View,ViewModel构成,M代表数据模型,V代表Ul组件,ViewModel是一个同步View和Model的对象
			</li>
			<li><strong>什么是MVC?</strong></li>
			<li>
				<b>MVC：</b>由View视图、Model模型、Controller控制器组成<b/>
				MVC可分为两种一个是通过View接受指令传递给Controller再改变Model,
				另一个是Controller接受指令传递给Model,再去改变View
			</li>
		</ul>

		<ul>
			<li><strong>Vue生命周期</strong></li>
			<li>
				beforeCreate、created、beforeMount、mounted、beforeUpdate、updated、beforeDestroy、destroyed
			</li>
		</ul>

		<ul>
			<li><strong>计算属性和Watch优先选择计算属性,因为计算属性是基于依赖进行缓存的</strong></li>
		</ul>

		<ul>
			<li><strong>Vue怎样会无法监听依赖数据？</strong></li>
			<li>
				1、当你利用索引直接设置一个项时,vm.items[2] = newValue;<br/>
				2、当你修改数组的长度时,vm.items.length = newLength 
			</li>
			<li>
				解决方法：<br/>
				Vue.set和splice
			</li>
		</ul>

		<ul>
			<li><strong>子父组件是怎么传递的?</strong></li>
			<li>
				父组件传递给子组件子组件通过props来接受父组件传递内容<br/>
				子组件传递给父组件是通过自定义事件,子组件通过$emit触发事件,父组件通过$on来监听事件
			</li>
		</ul>

		<ul>
			<li><strong>Vue的MVVM原理?</strong></li>
			<li>
				<textarea style="height:200px;">
					大致原理：
				    有三个函数对象一个是Observer管理数据模型的变更
				                  一个是Compile管理视图变更 
				                  一个是Watcher上以上两个的互通桥梁

				    Observer是监听数据对象的获取和设置工作,一旦有数据的获取或变更,会把这次行为当做是一个订阅者
				    存放到一个Dep对象里,订阅者其实就是Watcher,
				    触发Watcher的方式是通过对数据对象绑定Object.defineProperty,在getter方法下定义一个属性，
				    在Watcher每次实例化的时候就会把数据对象下getter下的属性指向自己,
				    Watcher获取到值后他会通知Complie这个对象对视图进行更新,
				    Compile对象是利用文档碎片,对模板里面的表达式进行正则匹配和指令进行解析从而更新视图
				</textarea>
			</li>
		</ul>

		<ul>
			<li><strong>对vue的认知</strong></li>
			<li>
				<textarea style="height:150px;">
					1、vue通过把真实的DOM树抽象成一棵javaScript抽象树,通过修改抽象树数据后,
						将抽象树转化成真实DOM重绘到页面上,它通过VNode节点模拟真实DOM,
						VNode性能的展现是通过diff算法进行计算,它通过对比同层节点，而非对树进行遍历搜索
					2、在列表渲染过程中,当列表数据发生变化时,为了避免大规模渲染,Vue会尽可能复用缓存frag,当数据对象为Array时,缓存id为数组的value,当数据对象为Object时,
					缓存id对象的$key,但是比如在数组中有重复相同的值,会出现缓存id冲突警告,会导致插入失败,这就是我们为什么会在v-for循环上加上key,它将使用数据的索引作为缓存id,
					(总结：为了避免大规模数据变化造成列表渲染,vue会可能复用相同的数据,会把数据值作用缓存id,但是有时会出现重复的值,造成id冲突,所以用在v-for循环上会把key当成缓存id)
				</textarea>
			</li>
		</ul>

		<ul>
			<li><strong>Vuex源码</strong></li>
			<li>
				<textarea style="height:100px;">
					vuex源码有将进一千行代码,里面分为几块，一块是定义了一些工具方法,一个Model类，一个Store类,
					页面进来先看是否安装了vuex,然后分版本去初始化vuex,挂载Store到根组件,方便统一访问,
					像commit、watch、dipsatch都是定义在Store原型方法上的
					Store类里定义一些属性，及调用Model类，Model类都是一些遍历action,getter之类的方法,
				</textarea>
			</li>
		</ul>

		<ul>
			<li><strong>vue开发过程遇到的问题</strong></li>
			<li>
				1、组件的嵌套过深，子组件要传递给最上面的父组件值时会传递不到<br/>
				2、我们在使用v-for进行渲染时，尽可能使用渲染元素自身属性的id给渲染的元素绑定一个key值，这样在当前渲染元素的DOM结构发生变化时，能够单独响应该元素而不触发所有元素的渲染
			</li>
		</ul>

		<ul>
			<li><strong>自定义组件怎样完善?</strong></li>
			<li>
				1、可以通用<br/>
				2、代码尽量简洁<br/>
				3、容易修改<br/>
				4、功能丰富
			</li>
		</ul>

		<ul>
			<li><strong>对vue的理解？</strong></li>
			<li>
				1、vue不必担心对dom操作,因为他靠数据驱动双向绑定<br/>
				2、组件化开发,让项目可拓展、可复用、重用性高<br/>
				3、单页应用体验好<br/>
				4、学习成本低小而轻量<br/>
			</li>
		</ul>

		<ul>
			<li><strong>vue-router有哪几种导航钩子?</strong></li>
			<li>
				三种：<br/>
				第1种：全局导航钩子点击导航前router.beforeEach(),点击导航后router.afterEach()<br/>
				第2种：组件内的钩子beforeRouteEnter、beforeRouteUpdate、beforeRouteLeave<br/>
				第3种：单独路由独享组件beforeEnter
			</li>
		</ul>

		<ul>
			<li><strong>v-if和v-show的区别</strong></li>
			<li>
				<b>共同点：</b>都是动态显示DOM元素<br/>
				<b>区别：</b><br/>
				1、v-if是动态向DOM添加或删除DOM元素,v-show是通过设置DOM的display样式控制显示隐藏<br/>
				2、<b>编译过程：</b>v-if切换有一个局部编译/卸载过程，切换过程中合适销毁和重建内部事件监听子组件,
				v-show只是简单的基于css切换<br/>
				3、<b>编译条件：</b>v-if是惰性的,如果初始条件为假,则什么也不做,v-show是在任何条件 下都会被编译<br/>
				4、<b>性能消耗：</b>v-if有更高的切换消耗,v-show有更高的初始渲染消耗<br/>
				5、<b>使用场景：</b>v-if适合运营条件不太可能改变,v-show适合频繁切换
			</li>
		</ul>
	</div>
</template>
<script>
</script>
<style lang="scss" type="text/css">
ul,li {
  margin: 0;
  padding: 10px;
  list-style-type: none;
}
ul {
  border:1px solid #000;
  margin: 20px 0;
}
strong {
    color: firebrick;
}
</style>
