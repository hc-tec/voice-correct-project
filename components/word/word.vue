<template>
	<view class="evaluate-word">
		<slot></slot>
	</view>
</template>

<script>
	export default {
		props: ["word"],
		data() {
			return {
				
			}
		}
	}
</script>

<style>
	.evaluate-word {
		font-size: 20px;
		padding: 3px;
		border-radius: 2px;
		color: var(--warning-color);
		border: 1px solid var(--warning-color);
		margin: 0 10px 5px 0;
	}
</style>
