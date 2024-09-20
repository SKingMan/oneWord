<template>
	
	<view class="container_word">
<uni-section title="笑口常开" type="line">
			<uni-card class="sao_card">
				<!-- <image slot='cover' style="width: 100%;" :src="top_image.url"></image> -->
				<text class="uni-body">{{jok_content}}</text>
				<view slot="actions" class="card-actions">
					<view class="card-actions-item" @click="actionsClick_share('分享')">
						<uni-icons type="pengyouquan" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">分享</text>
					</view>
					<view class="card-actions-item" @click="actionsClick_zan('点赞')">
						<uni-icons type="heart" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">点赞</text>
					</view>
					<view class="card-actions-item" @click="actionsClick_comment('评论')">
						<uni-icons type="chatbubble" size="18" color="#999"></uni-icons>
						<text class="card-actions-item-text">评论</text>
					</view>
				</view>
			</uni-card>
		</uni-section>
	</view>
	<view class="btn">
		<button @click="fetchcontent" >换一个</button>
	</view>
	<view>
		<!-- 提示信息弹窗 -->
		<uni-popup ref="message" type="message">
			<uni-popup-message :type="msgType" :message="messageText" :duration="2000"></uni-popup-message>
		</uni-popup>
	</view>



</template>

<script>
	export default {
		data() {
			return {
				jok_content: "",
				temp:{},
				top_image: {},
				indicatorDots:true,
				autoplay:true,
				interval: 2000,
				duration: 500,
				type: 'center',
				messageText: '这是一条成功提示',
			}
		},
		onReady() {},
		methods:{
				fetchcontent(){
					
					uni.request({
							url: "https://api.vvhan.com/api/text/joke?type=json",
							success: (res) => {
							  if (res.statusCode === 200) {
								this.temp = res.data;
								this.jok_content = this.temp.data.content; // 假设返回的数据是一个数组
								console.log(this.jok_content)
							  } else {
								console.error('请求成功但状态码不是 200:', res.statusCode);
							  }
							},
							fail: (err) => {
							  console.error('请求失败:', err);
							}
						  });
						  
				},
				fetchimage(){
					uni.request({
							url: "https://api.vvhan.com/api/wallpaper/views?type=json",
							success: (res) => {
							  if (res.statusCode === 200) {
								this.top_image = res.data; // 假设返回的数据是一个数组
								// console.log('类型:', Object.prototype.toString.call(this.top_image));
								// console.log(this.top_image);
							  } else {
								console.error('请求成功但状态码不是 200:', res.statusCode);
							  }
							},
							fail: (err) => {
							  console.error('请求失败:', err);
							}
						  });
				},

				actionsClick_share(type) {

					this.messageText = `自己多快乐一点吧~`
					this.$refs.message.open()
				},
				actionsClick_zan(type) {
				
					this.messageText = `hahah，喜欢 就记下来吧~`
					this.$refs.message.open()
				},
				actionsClick_comment(type) {
				
					this.messageText = `是滴，没有评论功能~`
					this.$refs.message.open()
				},
		
		},
		components:{
			
		},
		mounted(){
			this.fetchcontent();
			
		}
	}
</script>

<style lang="scss">
	.bander{
		width: 750rpx;
		height: 268rpx;
	}
	.container_word{
		width: 100%;
		padding-top: 100rpxS;
		.container_word_txt{
			padding: 10px;
			.container_card{
				height: 230rpx;
			}
		}
	}

	.btn{

		padding: 5px;
		color: #ffffff;
	}
	.container {
			overflow: hidden;
		}
	
		
		.cover-content {
			position: absolute;
			bottom: 0;
			left: 0;
			right: 0;
			height: 40px;
			background-color: rgba($color: #000000, $alpha: 0.4);
			display: flex;
			flex-direction: row;
			align-items: center;
			padding-left: 15px;
			font-size: 14px;
			color: #fff;
		}
	
		.card-actions {
			display: flex;
			flex-direction: row;
			justify-content: space-around;
			align-items: center;
			height: 45px;
			border-top: 1px #eee solid;
		}
		
		.no-border {
			border-width: 0;
		}
</style>
