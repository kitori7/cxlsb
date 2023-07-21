<template>
	<view class="detail">
		<template v-if="!isEmpty && articlesContet">
			<image class="img" :src="articlesContet.avatar"></image>
			<view class="content">
				<view class="title">
					{{articlesContet.title}}
				</view>
				<view class="description">
					<view class="icons"><u-icon name="account" size="21" color="#a3a3a3"></u-icon><text>发布者：xxx</text>
					</view>
					<view class="icons"><u-icon name="calendar" size="21"
							color="#a3a3a3"></u-icon><text>发布日期：{{dayjs(articlesContet.publish_date*1000).format("YYYY-MM-DD HH:mm") }}</text>
					</view>
				</view>
				<text>{{articlesContet.content}}</text>
			</view>
		</template>
		<u-empty text="" mode="data" v-else></u-empty>

	</view>
</template>

<script lang="ts" setup>
	import { onLoad } from "@dcloudio/uni-app"
	import { ref } from "vue"
	import dayjs from "dayjs"
	const db = uniCloud.database()

	interface IContent {
		_id : string;
		title : string
		content : string
		avatar : string
		publish_date : number
		excerpt : string
	}
	//获取文章内容
	const articlesId = ref<string>()
	const articlesContet = ref<IContent>()
	const isEmpty = ref<boolean>(true)
	onLoad(async ({ _id }) => {
		console.log(_id);
		if (_id === undefined) {
			isEmpty.value = true
		} else {
			isEmpty.value = false
			articlesId.value = _id
			const res = await db.collection('cxlsb-u-articles').doc(_id).get()
			articlesContet.value = res.result.data[0]
		}

	})
</script>

<style lang="scss">
	.detail {
		border: 1px solid transparent;

		.img {
			position: absolute;
			z-index: 0;
			height: 400rpx;
			width: 100vw;
			object-fit: cover;
		}

		.content {
			background-color: #fff;
			padding: 20rpx;
			margin-top: 400rpx;

			.title {
				font-size: 40rpx;
				font-weight: 700;
			}

			.description {
				margin: 20rpx 0;
				color: #a3a3a3;
				display: flex;
				justify-content: space-between;

				.icons {
					display: flex;
					align-items: center;
					justify-content: flex-start;
				}
			}
		}
	}
</style>