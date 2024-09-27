<style>
.ball {
	position: absolute;
	top: 275px;
	left: 950px;
	width: 30px;
	height: 30px;
	background-color: #EE6362;
	border-radius: 100%;
}

.demo {
	position: absolute;
	width: calc(100% - 60px);
}

.well {
	position: absolute;
	top: 89px;
	left: 682px;
	width: 119px;
	height: 37px;
	background-color: #A4ADB5;
}

.pillar {
	position: absolute;
	top: 94px;
	left: 671px;
	width: 11px;
	height: 37px;
	background-color: #A6B0B8;
}

.mappanel_box {
	position: relative;
	width: 1484px;
}

.lwell {
	position: absolute;
    top: 87px;
    left: 159px;
    width: 10px;
    height: 542px;
    background-color: #D1D8DE;
    transform: skew(-23deg, 0deg);
}
</style>

<template>
	<div class="mappanel">
		<div id="mappanel_box" class="mappanel_box">
			 <img class="demo" src="/images/dd.png" alt=""> 
			<!--<img class="demo" src="/images/tttt.stl" alt="">-->
			<div class="well"></div>
			<div class="pillar"></div>
			<div class="lwell"></div>
			<!-- <canvas ref="prismCanvas" width="1850" height="1100"></canvas> -->
			<!-- <div class="ball"></div> -->
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			wd: 110,//同一排 每一個的 位置
			pointData: [
				{ x: 730, y: 1050, w: 320, h: 20, d: 255, text: '物件1' },
			],
		}
	},
	created() {

	},
	mounted() {
	},
	methods: {
	}
};
</script>