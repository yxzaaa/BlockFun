<template>
	<view class="nav-bar-box" :style="{justifyContent:layout=='left'?'flex-start':'center'}">
		<view v-show="layout == 'left'" class="left-box">
			<view class="left-title">{{title}}</view>
			<view class="left-subtitle">{{subTitle}}</view>
		</view>
		<view class="center-box">
			<text
				v-show="layout == 'center'"
				class="nav-bar-title" 
				:style="{color:textColor}"
			>
				{{title}}
			</text>
		</view>
		<view
			:class="['back-btn','icon-box',buttons && buttons.back && buttons.back.type=='circle'?'circle':'']" 
			v-show="buttons && buttons.back"
			:style="{backgroundColor:buttons && buttons.back && buttons.back.type=='circle'?'rgba(0,0,0,'+(backOpacity-priviteOpacity)+')':'transparent'}"
		>
			<img class="icon-img" src="../../static/icons/back.png" alt="">
		</view>
		<view class="right-btn-list">
			<view 
				:class="['icon-box',buttons && buttons.love && buttons.love.type=='circle'?'circle':'']" 
				v-show="buttons && buttons.love"
				:style="{backgroundColor:buttons && buttons.love && buttons.love.type=='circle'?'rgba(0,0,0,'+(backOpacity-priviteOpacity)+')':'transparent'}"
			>
				<img class="icon-img" src="../../static/icons/love.png" alt="">
			</view>
			<view 
				:class="['icon-box',buttons && buttons.share && buttons.share.type=='circle'?'circle':'']" 
				v-show="buttons && buttons.share"
				:style="{backgroundColor:buttons && buttons.share && buttons.share.type=='circle'?'rgba(0,0,0,'+(backOpacity-priviteOpacity)+')':'transparent'}"
			>
				<img class="icon-img" src="../../static/icons/share.png" alt="">
			</view>
			<view 
				:class="['icon-box',buttons && buttons.cart && buttons.cart.type=='circle'?'circle':'']" 
				v-show="buttons && buttons.cart"
				:style="{backgroundColor:buttons && buttons.cart && buttons.cart.type=='circle'?'rgba(0,0,0,'+(backOpacity-priviteOpacity)+')':'transparent'}"
			>
				<img class="icon-img" src="../../static/icons/cart.png" alt="">
			</view>
			<view
				:class="['icon-box',buttons && buttons.search && buttons.search.type=='circle'?'circle':'']" 
				v-show="buttons && buttons.search"
				:style="{backgroundColor:buttons && buttons.search && buttons.search.type=='circle'?'rgba(0,0,0,'+(backOpacity-priviteOpacity)+')':'transparent'}"
			>
				<img class="icon-img" src="../../static/icons/search.png" alt="">
			</view>
			<view
				class="icon-text-box" 
				v-show="buttons && buttons.textbtn"
			>
				<text class="text-btn">{{buttons && buttons.textbtn && buttons.textbtn.text}}</text>
			</view>
		</view>
		<view class="nav-bg-block" :style="{opacity:priviteOpacity}"></view>
	</view>
</template>

<script>
	export default{
		props:{
			title:{
				type:String,
				default:''
			},
			subTitle:{
				type:String,
				default:'Unblockgrace'
			},
			textColor:{
				type:String,
				default:'#000000'
			},
			layout:{
				type:String,
				default:'center'
			},
			opacity:{
				type:Number,
				default:0
			},
			buttons:{
				type:Object
			}
		},
		data(){
			return {
				priviteOpacity:0,
				backOpacity:0.2
			}
		},
		watch:{
			opacity(val){
				this.priviteOpacity = (val/200).toFixed(2);
			}
		},
		mounted(){
		},
		methods:{
		}
	}
</script>

<style lang="scss" scoped>
	.nav-bar-box{
		position: fixed;
		top:0;
		left:0;
		width:100%;
		padding-top:28px;
		height:72px;
		z-index:10000;
		display:flex;
		align-items:center;
		.back-btn{
			position:absolute;
			bottom:4px;
			left:24upx;
		}
		.right-btn-list{
			position:absolute;
			bottom:4px;
			right:24upx;
			display:flex;
			justify-content:flex-end;
			align-items:center;
			.icon-box{
				margin-left:5px;
			}
		}
		.nav-bg-block{
			position: absolute;
			top:0;
			left:0;
			width:100%;
			height:100%;
			z-index:-1;
			background-image:url(../../static/bg.jpg);
			background-size:100% auto;
			background-repeat: no-repeat;
			background-color:#15030B;
			overflow: hidden;
		}
		.left-box{
			padding:0upx 30upx;
			.left-title{
				color:#fff;
				font-size: 18px;
				font-weight: bold;
			}
			.left-subtitle{
				color:#fff;
				font-size: 10px;
				padding-left:5upx;
			}
		}
		.center-box{
			
		}
		.icon-box{
			width:36px;
			height:36px;
			border-radius:18px;
			text-align:center;
			.icon-img{
				width:36px;
				height:36px;
				display: inline-block;
			}
		}
		.icon-text-box{
			height:36px;
			padding:0px 5px;
			.text-btn{
				line-height:36px;
				color:#DA53A2;
				font-size: 30upx;
			}
		}
		.icon-box.circle{
			background: rgba(0,0,0,.2);
		}
	}
</style>
