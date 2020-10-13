<template>
	<button 
		:class="'el-button '+typeClass"
		:style="{
			transform: activeTransformStyle
		}"
		@click="handleClick($event)"
		@touchstart="activeStart"
		@touchend="activeEnd">
		<slot></slot>
	</button>
</template>

<script>
	export default {
		name: 'el-button',
		
		props: {
			type: {
				type: String,
				default: ''
			},
		},
		
		data() {
			return {
				activeTransformStyle: ''
			};
		},
		computed: {
			typeClass() {
				return `${this.$options.name}--${this.type}`;
			}
		},
		
		methods: {
			handleClick(e) {
				this.$emit('click', e);
			},
			activeStart() {
				this.activeTransformStyle = 'scale(0.95)'
			},
			activeEnd() {
				this.activeTransformStyle = ''
			}
		}
	}
</script>

<style scoped>
	[class ~= el-button] {
		width: 150px;
		margin-top: 10px;	
		font-size: 14px;
		color: white;
		background-color: var(--primary-color);
		transition: transform .1s;
	}
	.el-button--success {
		background-color: var(--success-color);
	}
</style>
