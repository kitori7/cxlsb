<template>
	<view class="contract-list">
		<view class="menu">
			<u-collapse accordion :border="false">
				<u-collapse-item title="免费合同" name="Docs guide" :is-link="false">
					<text class="u-collapse-content">免费</text>
				</u-collapse-item>
			</u-collapse>
			<div class="qr-content">
				<view class="img" src="" alt=""></view>
				<text>客服电话：</text>
				<text>13923870065</text>
				<text>13823541128</text>
			</div>
		</view>
		<view class="content">
			<view class="img"></view>
			<div class="item-content">
				<div class="item">
					<div class="title">借条</div>
					<div class="price"><span>价格：￥0.00</span></div>
				</div>
				<div class="item">
					<div class="title">借条</div>
					<div class="price"><span>价格：￥0.00</span></div>
				</div>
			</div>
		</view>
	</view>
</template>

<script lang="ts" setup>
</script>

<style lang="scss">
	.contract-list {
		display: flex;
		background-color: #f5f5f5;

		.menu {
			width: 230rpx;
			height: calc(100vh - 88rpx);
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			background-color: #fff;

			.qr-content {
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				margin-bottom: 50rpx;

				.img {
					background-color: #666;
					width: 100rpx;
					height: 100rpx;
				}
			}
		}

		.content {
			flex: 1;
			margin-left: 15rpx;
			background-color: #fff;
			.img{
				box-sizing: border-box;
				padding: 10rpx;
				width: 100%;
				height: 150rpx;
				background-color: #666;
			}
			.item-content{
				padding: 20rpx;
				.item{
					display: flex;
					flex-direction: column;
					justify-content: center;
					line-height: 60rpx;
					height: 150rpx;
					border-bottom: 2rpx solid #dddddd;
					.price{
						color: #b8b8b8;
					}
				}
			}
		}
	}
</style>