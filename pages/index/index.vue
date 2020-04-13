<template>
	<view class="content">
		<!-- <view class="card" v-show="addShow"> -->
				<!-- <view class="close" @click="closeCard">^</view> -->
			<input type="text" placeholder="todos" class="border" adjust-position focus v-model="value"/>
		<!-- </view> -->
		<view>{{msg}}</view>
		<view class="add" @click="addTodo" ></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				addShow:false,
				value:'',
				msg:null
			}
		},
		onLoad() {
			console.log(0)
		},
		onShow() {
			let that = this
			uni.getStorage({
			    key: 'storage_key',
			    success: (res)=>{
							this.msg = res.data
			    }
			});
		},
		onHide() {
			console.log(3)
		},
		methods: {
		addTodo(e){
			console.log(e.target)
			// this.addShow = true
			uni.setStorage({
			    key: 'storage_key',
			    data: this.value,
					error:(err)=>{
						console.log(err)
					},
			    success:(res)=>{
			        console.log(res);
			    }
			});
		}
		}
	}
</script>

<style>
	.done{
		text-decoration: line-through;
	}
	.border{
		border-bottom: 1px solid #ccc;
	}
	/* .close{
		display: flex;
		width: 20px;
		height: 20px;
		color: #ccc;
		justify-content: center;
		align-content: center;
		border-radius: 5px;
		transform: rotate(180deg);
	} */
	.card{
		display: flex;
		flex-direction: column;
		position: absolute;
		z-index: 9;
		width: 80%;
		padding: 5px;
		border: 1px solid #ccc;
		border-radius: 20px;
		top: 0;
	}
	.add{
		width: 50px;
		height: 50px;
		border: 1px solid #ccc;
		border-radius: 50%;
		position: fixed;
		right: 10px;
		bottom: 100px;
		background: #1f7db1;
	}
	.add::after{
		content: '';
		height: 50%;
		border: 2px solid #fff;
		border-radius: 5px;
		position:absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%,-50%);
	}
	.add::before{
		content: '';
		height: 50%;
		border: 2px solid #fff;
		border-radius: 5px;
		position:absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%,-50%) rotate(90deg);
	}
	.add:hover{
		background: #ccc;
		transition: all ease-in-out 2s;
	}
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
