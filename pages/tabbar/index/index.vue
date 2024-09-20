<template>
	<view class="index_bander_box">
		<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
						:duration="duration" >
						<swiper-item @click="moviesHandle_america">
							<image class="bander" src="../../../static/image/1.jpg" mode=""></image>
						</swiper-item>
						<swiper-item @click="moviesHandle_pets">
							<image class="bander" src="../../../static/image/2.jpeg" mode=""></image>
						</swiper-item>
						<swiper-item @click="moviesHandle_jurassic">
							<image class="bander" src="../../../static/image/3.jpeg" mode=""></image>
						</swiper-item>
						
					</swiper>
	</view>
	<view class="container_word">
			<uni-section class="container_word_txt" title="每日一言" type="line">
				<uni-card shadow class="container_card">
					<text class="uni-body">{{jok_content}}</text>
				</uni-card>
			</uni-section>
	</view>
	<view class="btn">
		<button @click="fetchcontent" >换一个</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				jok_content: "",
				topBanner: {},
				indicatorDots:true,
				autoplay:true,
				interval: 2000,
				duration: 500
			}
		},
		methods:{
				fetchcontent(){
					uni.request({
							url: "https://api.vvhan.com/api/ian/rand",
							success: (res) => {
							  if (res.statusCode === 200) {
								this.jok_content = res.data; // 假设返回的数据是一个数组
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
							url: "https://api.vvhan.com/api/bing?type=json&rand=sj",
							success: (res) => {
							  if (res.statusCode === 200) {
								this.topBanner = res.data; // 假设返回的数据是一个数组
								// console.log('类型:', Object.prototype.toString.call(this.topBanner));
								// console.log(this.topBanner);
							  } else {
								console.error('请求成功但状态码不是 200:', res.statusCode);
							  }
							},
							fail: (err) => {
							  console.error('请求失败:', err);
							}
						  });
				},
				moviesHandle_america(){
					
					uni.navigateTo({
						url:"/pages/movies/America/America"
					})
				},
				moviesHandle_pets(){
					
					uni.navigateTo({
						url:"/pages/movies/pets/pets"
					})
				},
				moviesHandle_jurassic(){
					
					uni.navigateTo({
						url:"/pages/movies/jurassic/jurassic"
					})
				},
		},
		components:{
			
		},
		mounted(){
			this.fetchcontent();
			this.fetchimage();
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
