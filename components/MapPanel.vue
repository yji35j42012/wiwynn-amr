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
</style>

<template>
	<div class="mappanel">
		<div id="mappanel_box" class="mappanel_box">
			<canvas ref="prismCanvas" width="1850" height="1100"></canvas>
			<div class="ball"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			wd: 110,//同一排 每一個的 位置
			pointData: [
				// { x: 1410, y: 780, w: 80, h: 20, d: 60, text: '物件1' },

			],
		}
	},
	created() {
		for (var i=0; i<10; i++) {
			this.pointData.push(
				{ x: i*110+70, y: 400-35*i, w: 80, h: 20, d: 60, text: '物件1' },
				{ x: i*110+170, y: 500-35*i, w: 80, h: 20, d: 60, text: '物件1' },
				{ x: i*110+470, y: 800-35*i, w: 80, h: 20, d: 60, text: '物件1' }
			)
		}
		for (var i=0; i<9; i++) {
			this.pointData.push(
				{ x: i*110+270+110, y: 600-35-35*i, w: 80, h: 20, d: 60, text: '物件1' },
				{ x: i*110+370+110, y: 700-35-35*i, w: 80, h: 20, d: 60, text: '物件1' },
			)
		}
		for (var i=0; i<4; i++) {
			this.pointData.push(
				{ x: i*110+570, y: 900-35*i, w: 80, h: 20, d: 60, text: '物件1' },
				{ x: i*110+670, y: 1000-35*i, w: 80, h: 20, d: 60, text: '物件1' },

				{ x: i*110+1230, y: 900-210-35*i, w: 80, h: 20, d: 60, text: '物件1' },
				{ x: i*110+1330, y: 1000-210-35*i, w: 80, h: 20, d: 60, text: '物件1' },
			);
		}
	},
	mounted() {
		this.pointData.forEach(item => {
			this.drawPrism(item.x, item.y, item.w, item.h, item.d);
		});
	},
	methods: {
		drawLine(ctx, x1, y1, x2, y2) {
			ctx.beginPath();
			ctx.moveTo(x1, y1);
			ctx.lineTo(x2, y2);
			ctx.stroke();
		},
		drawPrism(xn, yn, w, h, d) {
			const canvas=this.$refs.prismCanvas;
			const ctx=canvas.getContext('2d');
			const x=xn, y=yn, width=w, height=h, depth=d;

			const skew=depth/2.5;
			const offset=depth/1.414;

			// Draw front face (as a parallelogram)
			ctx.strokeStyle='#DCDCDC';
			ctx.fillStyle='#ECECEC';
			ctx.beginPath();
			ctx.moveTo(x, y);
			ctx.lineTo(x+width, y-skew);
			ctx.lineTo(x+width, y+height-skew);
			ctx.lineTo(x, y+height);
			ctx.closePath();
			ctx.fill();
			ctx.stroke();

			// Draw top face
			ctx.fillStyle='#ffffff';
			ctx.beginPath();
			ctx.moveTo(x, y);
			ctx.lineTo(x-offset, y-offset);
			ctx.lineTo(x+width-offset, y-offset-skew);
			ctx.lineTo(x+width, y-skew);
			ctx.closePath();
			ctx.fill();
			ctx.stroke();

			// Draw left face
			ctx.fillStyle='#ECECEC';
			ctx.beginPath();
			ctx.moveTo(x, y);
			ctx.lineTo(x-offset, y-offset);
			ctx.lineTo(x-offset, y+height-offset);
			ctx.lineTo(x, y+height);
			ctx.closePath();
			ctx.fill();
			ctx.stroke();

			// Draw edges
			this.drawLine(ctx, x, y, x-offset, y-offset);
			this.drawLine(ctx, x, y+height, x-offset, y+height-offset);
			this.drawLine(ctx, x+width, y-skew, x+width-offset, y-offset-skew);
		}
	}
};
</script>