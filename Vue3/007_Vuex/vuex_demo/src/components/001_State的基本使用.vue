<template>
	<div class="app">
		<!-- <h4>当前计数：{{ $store.state.counter }}</h4> -->
		<h4>当前计数：{{ counter }}</h4>
		<h4>当前年龄：{{ age }}</h4>

		<button @click="increment">+1</button>
		<button @click="decrement">-1</button>
	</div>
</template>

<script setup>
	import { toRefs } from 'vue';
	import { useStore } from 'vuex';

	const store = useStore();

	// 在setup中推荐通过toRefs将store.state中的数据解构出来，这样数据依然具有响应式
	let { counter, age } = toRefs(store.state);

	function increment() {
		store.commit('increment');
	}
	function decrement() {
		store.commit('decrement');
	}
</script>

<style lang="less" scoped></style>
