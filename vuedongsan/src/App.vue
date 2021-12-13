<template>

<div class="modal" v-if="isDetailModalShows[0] == 1">
	<div class="dim"></div>
	<div class="box">
		<h2>상세페이지</h2>
		<p>상세 설명</p>
	</div>
</div>

<nav class="menu">
	<ul>
		<li v-for="(menu, i) in menus" :key="i">
			<a href="javsacript:;">{{ menu }}</a>
		</li>
	</ul>
</nav>
<div class="products">
	<ul>
		<li v-for="(loc, i) in products" :key="i">
			<img src="./assets/img01.jpg" @click="isDetailModalShows[0] = 1">
			<strong>{{ loc }} 원룸</strong>
			<p><span :style="style">{{ price1 }}</span> 만원</p>
			<button @click="increase(i)">허위매물신고</button> <span>신고 수 : {{ declarations[i] }}</span>
		</li>
	</ul>
</div>
</template>

<script>
export default {
name: 'App',
data(){
	return {
		isDetailModalShows : [0, 0, 0],
		price1 :  60,
		price2 :  40,
		style : 'font-weight:600',
		menus : ['메인', '목록', '문의'],
		products : ['역삼동', '천호동', '마포구'],
		declarations : [0, 0, 0],
	}
},
methods: {
	increase(i){
		this.declarations[i]++
	}
},
components: {
}
}
</script>

<style>
#app {
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
}
.products ul li {padding:15px; list-style:none;}
.products ul li + li {border-top:1px solid #ddd;}
.products ul li img {display:block; margin:0 auto 10px; width:400px;}
.modal {display:none; position:fixed;}
.modal .dim {position:fixed; left:0; top:0; width:100%; height:100%; background:rgba(0,0,0,.7);}
.modal .box {position:fixed; left:50%; top:50%; padding:20px; min-width:80%; max-width:1000px; transform:translate(-50%, -50%); background:#fff;}
</style>
