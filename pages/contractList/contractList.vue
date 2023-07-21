<template>
	<view class="contract-list">
		<view class="menu">
			<view class="tab-content">
				<text :class="{'active': type ===1}" @click='handleChange(1)'>常用合同</text>
				<text :class="{'active': type ===2}" @click='handleChange(2)'>高级合同</text>
			</view>

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
				<div class="item" v-for="item in contractList" :key="item._id">
					<div class="title">{{item.name}}</div>
					<div class="price"><span>价格：￥{{(item.price / 100).toFixed(2)}}</span></div>
				</div>
			</div>
		</view>
	</view>
</template>

<script lang="ts" setup>
	import { onMounted, ref } from "vue"
	const db = uniCloud.database()

	//获取数据
	const contractList = ref()
	const type = ref<number>(0)
	onMounted(() => {
		db.collection('cxlsb-u-contract').get().then((res) => {
			contractList.value = res.result.data
		})
	})
	//tab点击事件
	function handleChange(index : number) {
		type.value = index
		db.collection('cxlsb-u-contract').where(`type==${type.value}`).get().then((res) => {
			contractList.value = res.result.data
		})
	}
</script>

<style lang="scss">
	.contract-list {
		display: flex;
		background-color: #f5f5f5;

		.menu {
			width: 230rpx;
			height: 100vh;
			display: flex;
			flex-direction: column;
			justify-content: space-between;
			background-color: #fff;

			.tab-content {
				display: flex;
				flex-direction: column;

				text {
					text-align: center;
					height: 100rpx;
					line-height: 100rpx;

					&.active {
						background-color: #f5f5f5;
					}
					
				}
			}

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

			.img {
				box-sizing: border-box;
				margin: 10rpx;
				width: calc(100% - 20rpx);
				height: 150rpx;
				background-color: #666;
			}

			.item-content {
				padding: 20rpx;

				.item {

					display: flex;
					flex-direction: column;
					justify-content: center;
					line-height: 60rpx;
					height: 150rpx;
					border-bottom: 2rpx solid #dddddd;

					.title {
						font-size: 30rpx;
					}

					.price {
						font-size: 28rpx;
						color: #b8b8b8;
					}
				}
			}
		}
	}
</style>