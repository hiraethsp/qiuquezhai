<template>
	<view>
		<view>因时间紧促，实现效果仅供参考，</view>
	<view class="top">
		<text class="fanhui" v-if="index>0" @click="fanhui(list[index].pre)">返回</text>
		<text class="guanli">管理</text>
	</view>
	<view v-if="list[index].type==1&&index!=0" class="topic">【{{list[index].thisType}}】{{list[index].text}}</view>
	<view class="container">
		<view v-if="list[index].type==1" v-for="val in list" :key="index" class="content">
			<view class="contentBox" v-if="index==val.pre" @click="changeIndex(val.index)">
				<view v-if="val.type==1" class="contentText">【{{val.thisType}}】 {{val.text}}</view>
				<view v-else-if="val.type==2" class="contentText"><p>【{{val.thisType}}】 {{val.name}} {{val.writer}}</p>
				<p>{{val.content[0].text}}</p>
				</view>
			</view>
		</view>
		<view v-else-if="list[index].type==2" 
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index:0,
				list:[
				{//type=1为文件夹，type=2为文件。为文件夹时，content为内容文件/文件夹,pre为上级文件夹。
					index:0,
					type:1,
					pre:-1,
					content:[1,2],
					thisType:"",
					text:""
				},
				{
					index:1,
					type:1,
					pre:0,
					content:[3,4],
					thisType:"诗集",
					text:"杜牧诗"
				},
				{
					index:2,
					type:1,
					pre:0,
					content:[],
					thisType:"词集",
					text:"苏轼词"
				},
				{
					index:3,
					type:1,
					pre:1,
					content:[5,6],
					thisType:"律诗集",
					text:"杜牧诗"
				},
				{
					index:4,
					type:1,
					pre:1,
					content:[],
					thisType:"绝句集",
					text:"杜牧诗"
				},
				{
					index:5,
					type:2,
					pre:3,
					fcomment:"依依惜别，黯然销魂。",
					content:[{
						text:"多情却似总无情",
						punctuation:",",
						comment:"相聚如胶似漆却叹无情别去。"
					},
					{
						text:"唯觉樽前笑不成",
						punctuation:"。",
						comment:""
					},{
						text:"蜡烛有心还惜别",
						punctuation:",",
						comment:""
					},{	
						text:"替人垂泪到天明",
						punctuation:"。",
						comment:""
					}],
					thisType:"绝句",
					name:"赠别",
					writer:"杜牧"
				},
				{
					index:5,
					type:2,
					pre:3,
					fcomment:"",
					content:[{
						text:"银烛秋光冷画屏",
						punctuation:",",
						comment:""
					}],
					thisType:"绝句",
					name:"秋夕",
					writer:"杜牧"
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			fanhui: function(value){
				this.$data.index=value;
			},
			changeIndex:function(value){
				//不知道为什么value一直为0，先这么写。
				if(value==0) value=1;
				else if(value==1) value=3;
				else if(value==3) value=5;
				this.$data.index=value;
				console.log(value);
			}
		}
	}
</script>

<style>
	.top{
		position:fixed;
		width:100%;
		height:38px;
		margin-bottom:41px;
		top:53px;
		z-index: 100;
	}
	.fanhui{
		position: absolute;
		left: 10%;
		width: 100px;
		height: 38px;
		opacity: 1;
		
		font-family: Fotor HelloFont GongYiTi;
		font-size: 36px;
		font-weight: normal;
		text-align: center;
		letter-spacing: 0em;
		
		color: rgba(57, 157, 185, 0.8);
	}
	.guanli{
		position: absolute;
		right:10%;
		width: 100px;
		height: 38px;
		opacity: 1;
		
		font-family: Fotor HelloFont GongYiTi;
		font-size: 36px;
		font-weight: normal;
		text-align: center;
		letter-spacing: 0em;
		
		color: rgba(57, 157, 185, 0.8);
	}
	.topic{
		position: absolute;
		left: 30px;
		top: 110px;
		width: 327px;
		height: 58px;
		opacity: 1;
		
		font-family: Fotor HelloFont GongYiTi;
		font-size: 36px;
		font-weight: normal;
		text-align: center;
		letter-spacing: 0em;
		
		color: #3D3D3D;
	}
	.container{
		position:absolute;
		top:160px;
		height:70%;
		width:100%;
		padding-left: 10%;
		padding-right: 10%;
		overflow: scroll;
		/* background-color: red; */
	}
	.contentBox{
		margin-top: 20px;
		margin-bottom: 20px;
		width: 80%;
		height: 98px;
		border-radius: 10px;
		opacity: 1;
		
		background: rgba(179, 178, 178, 0.6);
	}
	.contentText{
		position: relative;
		left: 10%;
		top: 10px;
		width: 254px;
		height: 54px;
		opacity: 1;
		
		font-family: Fotor HelloFont GongYiTi;
		font-size: 24px;
		font-weight: normal;
		line-height: 30px;
		text-align: center;
		letter-spacing: 0em;
		
		color: #3D3D3D;
	}
</style>
