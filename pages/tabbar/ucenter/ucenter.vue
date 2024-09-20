<template>
  <view class="userlayout">
	  <view class="userinfo">
		  <view class="avatar">
			  <image src="../../../static/image/head.jpeg" mode="aspectFill"></image>
		  </view>
		  <view class="username">一言</view>
		  <view class="address">来自于：河南</view>
	  </view>
	  <view class="section">
		  <view class="list">
			  <!-- 这里不应该是循环，而应该是三段代码，因为图标和点击后跳转的链接不同 -->
			  <view class="row" v-for="item in 3">
				  <view class="left">
					<uni-icons type="download-filled" size="20" color="#00b783"></uni-icons>
					<view class="text">我的下载</view>
				  </view>
				  <view class="right">
					  <view class="text">0</view>
					  <uni-icons type="right" size="20" color="#aaa"></uni-icons>

				  </view>
			  </view>
		  </view>
	  </view>
	  <view class="section">
		  <view class="list">
		  			  <view class="row" v-for="item in 2">
		  				  <view class="left">
		  					<uni-icons type="download-filled" size="20" color="#00b783"></uni-icons>
		  					<view class="text">我的下载</view>
		  				  </view>
		  				  <view class="right">
		  					  <view class="text">0</view>
		  					  <uni-icons type="right" size="20" color="#aaa"></uni-icons>
		  
		  				  </view>
		  			  </view>
		  </view>
	  </view>
  </view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods:{
			
		},
		components:{
			
		},
		mounted(){

		}
	}
</script>

<style lang="scss" scoped>
.userlayout{
	.userinfo{
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		padding: 50rpx 0;
		.avatar{
			width: 160rpx;
			height: 160rpx;
			border-radius: 50%;
			overflow: hidden;
			image{
				width: 100%;
				height: 100%;
			}

		}
		.username{
			font-size:44rpx;
			color:#333;
			padding: 20rpx 0 5rpx;
		}
		.address{
			font-size: 28rpx;
			color:#aab;
		}
	}
	.section{
		width: 690rpx;
		margin: 50rpx auto;
		border: 1px solid #eee;
		border-radius: 10rpx;
		box-shadow: 0 0 30rpx rgba(0,0,0,0.05);
		.list{
			.row{
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 0 30rpx;
				height: 100rpx;
				border-bottom: 1px solid #eee;
				&:last-child{border-bottom: 0};
				.left{
					display: flex;
					align-items: center;
					.text{
						padding-left: 20rpx;
						color: #666;
					}
				}
				.right{
					display: flex;
					align-items: center;
					.text{
						padding-left: 28rpx;
						color: #aaa;
					}
				}
			}
		}
	}
}

</style>