<template>
	<view>
		{{ curWord }}
	</view>
</template>

<script>
	import global from '../../common/global.js'
	export default {
		data() {
			return {
				preWord: global.getPrevWord(),
				curWord: global.getCurrentWord(),
				nxtWord: global.getNextWord(),
			}
		},
		mounted() {
			setInterval(() => {
				this.curWord = global.getNextWord()
			}, 500)
			
		},

	}
</script>

<style>
</style>
