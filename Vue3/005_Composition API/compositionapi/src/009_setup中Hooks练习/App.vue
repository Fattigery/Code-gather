<template>
	<div>
		<!-- 计数器案例 -->
		<h4>当前计数：{{ counter }}</h4>
		<button @click="increment">+1</button>
		<button @click="decrement">-1</button>

		<hr />

		<!-- 修改title -->
		<div class="changeTitle" style="margin-top: 10px">
			<button @click="title = '首页 - 流行'">首页 - 流行</button>
			<button @click="title = '首页 - 热门'">首页 - 热门</button>
			<button @click="title = '首页 - 歌单'">首页 - 歌单</button>
			<button @click="changeTitle">首页 - 推荐</button>
		</div>

		<!-- 获取页面滚动位置 -->
		<h4>X：{{ scrollPosition.x }}</h4>
		<h4>Y：{{ scrollPosition.y }}</h4>
		<div class="scroll" style="width: 3000px; height: 2200px"></div>
	</div>
</template>

<script>
	import useCounter from './Hooks/useCounter.js';
	import useTitle from './Hooks/useTitle.js';
	import useScrollPosition from './Hooks/useScrollPosition';
	export default {
		setup() {
			// let { counter, increment, decrement } = useCounter(10);
			// 初始化页面标题
			let title = useTitle('App首页');

			// 一般useTitle在一个setup中调用一次就可以了，当需要再次修改，直接修改.value即可。
			function changeTitle() {
				title.value = '首页 - 推荐';
			}

			let scrollPosition = useScrollPosition();

			return {
				// counter,
				// increment,
				// decrement
				...useCounter(12),
				title,
				changeTitle,
				scrollPosition
			};
		}
	};
</script>

<style scoped></style>
