<template>
	<div class="app">
		<room-area :area-data="highScore"></room-area>
	</div>
</template>

<script setup>
	import { ref } from 'vue';
	import RoomArea from './components/RoomArea.vue';

	// 1.获取数据
	// JSON文件可以直接import导入
	// import highScore from './data/high_score.json';
	// console.log(highScore);

	// 模拟网络请求数据
	const highScore = ref({});

	setTimeout(() => {
		import('./data/high_score.json').then(res => {
			console.log(res.default);
			highScore.value = res.default;
		});
	}, 1000);
</script>

<style lang="less" scoped>
	.app {
		width: 1032px;
		margin: 0 auto;
		padding-top: 40px;
	}
</style>
