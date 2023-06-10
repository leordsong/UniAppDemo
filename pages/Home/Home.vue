<template>
	<view class="page">
		<view class="top-cover">
			<image class="cover-image" mode="aspectFill" src="../../static/home/milo2.jpg">
			</image>
		</view>
		
		<uni-search-bar
			radius="100" clearButton="none" cancelButton="none" class="search-bar" @focus="focus" :focus="searchFocus" @cancel="cancel"
			@search="search"
		>
		</uni-search-bar>
		
		<view class="search-bar-ext" v-if="searchFocus">
		    
		    <!-- Segmented Control -->
		    <uni-segmented-control class="segments"
				:current="current" :values="items" borderColor="#fc0c5a" activeColor="#fc0c5a"
				radius="100"
			>
		      <uni-segmented-control-item label="服务"></uni-segmented-control-item>
		      <uni-segmented-control-item label="时间"></uni-segmented-control-item>
		      <uni-segmented-control-item label="对象"></uni-segmented-control-item>
		    </uni-segmented-control>
		    
		    <!-- Icons -->
		    <view class="icons-container">
				<view class="icon-item">
				    <uni-icons type="star" size="50" color="#007AFF"></uni-icons>
				    <text>日托</text>
				</view>
				<view class="icon-item">
				    <uni-icons type="circle" size="50" color="#007AFF"></uni-icons>
				    <text>上门喂养</text>
				</view>
				<view class="icon-item">
				    <uni-icons type="home" size="50" color="#007AFF"></uni-icons>
				    <text>寄养</text>
				</view>
				<view class="icon-item">
				    <uni-icons type="map" size="50" color="#007AFF"></uni-icons>
				    <text>上门遛狗</text>
				</view>
		    </view>
		  </view>
		
		<uni-card padding="0" spacing="0" class="curved">
			<template v-slot:cover>
				<view class="custom-cover">
					<image class="cover-image" mode="aspectFill" src="../../static/home/cats.jpg">
					</image>
					<view class="cover-content">
						<text class="uni-subtitle uni-white">成功案例</text>
					</view>
				</view>
			</template>
		</uni-card>
		
		<uni-card padding="0" spacing="0" class="curved">
			<template v-slot:cover>
				<view class="custom-cover">
					<image class="cover-image" mode="aspectFill" src="../../static/home/pets.jpg">
					</image>
					<view class="cover-content">
						<text class="uni-subtitle uni-white">平台优势</text>
					</view>
				</view>
			</template>
		</uni-card>
	</view>
</template>

<script>
	export default {
		components: {},
		data() {
			return {
				searchFocus: false,
				items: ['服务', '时间', '对象'],
			}
		},
		methods: {
			onClick(e) {
				console.log(e)
			},
			actionsClick(text) {
				uni.showToast({
					title: text,
					icon: 'none'
				})
			},
			focus(e) {
				this.searchFocus = true
			},
			cancel(e) {
				this.searchFocus = false
			},
			search(res) {
				this.searchFocus = false
			},
		}
	}
</script>

<style lang="scss">
	
	.top-cover {
		flex: 1;
		flex-direction: row;
		position: relative;
		
		.cover-image {
			width: 100%;
			height: 250px;
			border-bottom-right-radius: 20px;
			border-bottom-left-radius: 20px;
		}
	}
	
	.search-bar {
		top: -20px;
		padding: 0 20px;
	}
	
	@keyframes fadein {
	  from {
	    opacity: 0;
	  }
	  to {
	    opacity: 1;
	  }
	}
	
	.search-bar-ext {
		animation: fadein 1s linear forwards;
		z-index: 9;
		position: absolute;
		padding: 5px 1px 30px 1px;
		background-color: white;
		border-bottom-right-radius: 15px;
		border-bottom-left-radius: 15px;
		left: 10px;
		right: 10px;
		box-shadow: 0 4px 0px 0 rgba(0, 0, 0, 0.2);
		
		.segments {
			margin-bottom: 30px;
		}
	
		.icons-container {
		  display: flex;
		  justify-content: space-around;
		  margin-top: 20px;
		  margin-bottom: 10px;
		  
		  .icon-item {
			display: flex;
			flex-direction: column;
			align-items: center;
			text-align: center;
		  }
		}
	}
	
	.curved {
		border-radius: 15px;
	}
	
	.custom-cover {
		flex: 1;
		flex-direction: row;
		position: relative;
		height: 280px;
		
		.cover-content {
			position: absolute;
			bottom: 4px;
			left: 0;
			right: 0;
			height: 40px;
			display: flex;
			flex-direction: row;
			align-items: center;
			padding-left: 15px;
			font-size: 30px;
			color: #fff;
		}
		
		.cover-image {
			width: 100%;
			height: 280px;
		}
	}
</style>
