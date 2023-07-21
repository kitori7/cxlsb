 <template>
 	<view class="honesty">
 		<u-list>
 			<u-list-item>
 				<div class="item">
 					<div class="content">
 						<view class="img"></view>
 						<div class="introduce-content">
 							<view class="title">最高人民法院关于审理国家赔偿案件确定精神损责任适用法律若干问</view>
 							<view class="p">最高人民法院关于审理国家赔偿案件确定精神损害赔偿责任适用法律若干问题的解释</view>
 						</div>
 					</div>
 					<div class="date">2023-04-03 10：39</div>
 				</div>
			<div class="item">
				<div class="content">
					<view class="img"></view>
					<div class="introduce-content">
						<view class="title">最高人民法院关于审理国家赔偿案件确定精神损责任适用法律若干问</view>
						<view class="p">最高人民法院关于审理国家赔偿案件确定精神损害赔偿责任适用法律若干问题的解释</view>
					</div>
				</div>
				<div class="date">2023-04-03 10：39</div>
			</div>
 			</u-list-item>
 		</u-list>
 	</view>
 </template>

 <script lang="ts" setup>

 </script>

 <style lang="scss">
 	.honesty {
		background-color: #f5f5f5;

 		.item {
 			height: 200rpx;
 			margin: 20rpx;
 			display: flex;
 			flex-direction: column;
 			padding: 20rpx 40rpx;
 			background-color: #fff;
			border-radius: 30rpx;
 			.content {
 				display: flex;
 				height: 80%;

 				.img {
 					background-color: #666;
 					width: 500rpx;
 					height: 132rpx;
					border-radius: 30rpx;
 				}

 				.introduce-content {
					margin-left: 20rpx;
 					.title {
						font-size: 35rpx;
 						overflow: hidden;
 						text-overflow: ellipsis;
 						display: -webkit-box;
 						-webkit-line-clamp: 1;
 						line-clamp: 1;
 						-webkit-box-orient: vertical;
 					}
					.p{
							font-size: 35rpx;
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
			.date{
				color: #707070;
				font-size: 28rpx;
				margin-left:  200rpx;
			}
 		}
 	}
 </style>