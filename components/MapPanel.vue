<template>
	<div class="mappanel">
		<div id="mappanel_box" class="mappanel_box">
			<canvas ref="prismCanvas" width="500" height="500"></canvas>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			pointData: [
				{ x1: 900, y1: 100, x2: 80, y2: 75, text: '巡邏點1' },
			],
		}
	},
	created() {

	},
	mounted() {
		this.drawPrism();
	},
	methods: {
		drawLine(ctx, x1, y1, x2, y2) {
			ctx.beginPath();
			ctx.moveTo(x1, y1);
			ctx.lineTo(x2, y2);
			ctx.stroke();
		},
		drawPrism() {
			const canvas=this.$refs.prismCanvas;
			const ctx=canvas.getContext('2d');
			const x=200, y=200, width=100, height=20, depth=80;
			const skew=depth/6;
			const offset=depth/2;

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