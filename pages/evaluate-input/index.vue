<template>
	<view class="evaluate-wrapper">
		<view class="evaluate-input-content">
			<text>请输入需要测评的汉字</text>
			<input 
				class="evaluate-input" 
				type="text" 
				maxlength="1"
				v-model="targetWord"
				:style="{
					borderBottom: inputBorderBottom
				}"
				@focus="inputHover"
				@blur="inputBlur "/>
			<el-button @click="add">添加</el-button>
			<el-button type="success" @click="startEvaluate">开始测评</el-button>
		</view>
		
		<view class="evaluate-results" v-if="globalData.targetWords.length">
			<text>已添加测评的汉字</text>
			<view class="evaluate-words">
				<word v-for="word in globalData.targetWords" :key="word">
					{{ word }}
				</word>
			</view>
			<view class="evaluate-clear" @click="$refs.popup.open()">清空</view>
		</view>
		<uni-popup-dialog 
			ref="popup"
			title="Warning" 
			content="确认清空输入的汉字吗？"
			@confirm="clear">
		</uni-popup-dialog>
	</view>
</template>

<script>
	import global from '../../common/global.js'
	export default {
		data() {
			return {
				targetWord: '',
				inputBorderBottom: '1px solid #000',
				globalData: global
			}
		},
		methods: {
			inputHover() {
				this.inputBorderBottom = '2px solid var(--primary-color)';
			},
			inputBlur() {
				this.inputBorderBottom = '1px solid #000';
			},
			add() {
				if(this.targetWord.length) {
					global.targetWords.push(this.targetWord)
					this.targetWord = ''
				}
			},
			startEvaluate() {
				if(global.targetWords.length) {
					uni.navigateTo({
						url: '/pages/evaluate-main/index'
					});
				}
			},
			clear() {
				global.targetWords = []
			}
		},
	}
</script>

<style>
	text {
		color: var(--primary-color);
	}
	.evaluate-wrapper {
		width: 60%;
		margin: 0 auto;
		padding: 10% 0;
	}
	.evaluate-wrapper > view {
		width: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.evaluate-input-content {
		margin-bottom: 10%;
	}
	.evaluate-input {
		width: 60px;
		padding: 10px;
		font-size: 20px;
		border-radius: 5px;
		text-align: center;
		transition: all .1s;
	}
	.evaluate-results,
	.evaluate-words {
		width: 100%;
	}
	.evaluate-results text {
		color: #000;
		margin-bottom: 10px;
	}
	.evaluate-words {
		display: flex;
		flex-wrap: wrap;
	}
	.evaluate-clear {
		margin-top: 20px;
		color: var(--danger-color);
		font-size: 14px;
	}
</style>
