 <template>
 	<view class="honesty">
 		<u-list>
 			<u-list-item>
 				<div class="item" v-for="item in articles" :key="item._id" @click="handleNavigateTo(item._id)">
 					<div class="content">
 						<view class="img">
 							<image :src="item.avatar.url" mode="aspectFill"></image>
 						</view>
 						<div class="introduce-content">
 							<view class="title">{{item.title}}</view>
 							<view class="p">{{item.content}}</view>
 						</div>
 					</div>
 					<div class="date">{{dayjs(item.publish_date).format("YYYY-MM-DD HH:mm") }}</div>
 				</div>
 			</u-list-item>
 		</u-list>
 	</view>
 </template>

 <script lang="ts" setup>
	import { ref, onMounted } from "vue"
	import dayjs from "dayjs"
	const db = uniCloud.database()
	//拉取数据
	const articles = ref()
	onMounted(async () => {
		const data = await db.collection('cxlsb-u-articles').where("article_status==1").get()
		articles.value = data.result.data
	})

	//跳转
	function handleNavigateTo(_id : number) {
		uni.navigateTo({
			url:`/pages/detail/detail?_id=${_id}`
		})
	}
 </script>

 <style lang="scss">
 	.honesty {
 		background-color: #f5f5f5;

 		.item {
 			height: 200rpx;
 			margin: 10rpx 20rpx;
 			display: flex;
 			flex-direction: column;
 			padding: 20rpx 30rpx;
 			background-color: #fff;
 			border-radius: 30rpx;

 			.content {
 				display: flex;
 				height: 160rpx;

 				.img {
 					background-color: #666;
 					width: 180rpx;
 					height: 140rpx;
 					border-radius: 30rpx;

 					image {
 						border-radius: 30rpx;
 						width: 100%;
 						height: 100%;
 						object-fit: cover;
 					}
 				}

 				.introduce-content {
 					margin-left: 20rpx;
 					flex: 1;
 					line-height: calc(140rpx / 3);

 					.title {
 						font-size: 28rpx;
 						overflow: hidden;
 						text-overflow: ellipsis;
 						display: -webkit-box;
 						-webkit-line-clamp: 1;
 						line-clamp: 1;
 						-webkit-box-orient: vertical;
 					}

 					.p {
 						font-size: 28rpx;
 						color: #707070;
 						overflow: hidden;
 						text-overflow: ellipsis;
 						display: -webkit-box;
 						-webkit-line-clamp: 2;
 						line-clamp: 2;
 						-webkit-box-orient: vertical;
 					}

 				}

 			}

 			.date {
 				color: #707070;
 				font-size: 20rpx;
 				margin-left: 200rpx;
 			}
 		}
 	}
 </style>