<script>

	export default {
		globalData: {
			targetWords: [],
			wordCounter: 0, // 记录当前汉字的索引值
			getCurrentWord() {
				return getApp().globalData.targetWords[getApp().globalData.wordCounter]
			},
			getNextWord() {
				if(getApp().globalData.wordCounter < getApp().globalData.targetWords.length-1) {
					getApp().globalData.wordCounter++
				}
				return getApp().globalData.getCurrentWord()
			},
			getPrevWord() {
				if(getApp().globalData.wordCounter > 0) {
					getApp().globalData.wordCounter--
				}
				return getApp().globalData.getCurrentWord()
			}
		},
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	body {
		--primary-color: #409EFF;
		--success-color: #67C23A;
		--warning-color: #E6A23C;
		--danger-color: #F56C6C;
	}
</style>
