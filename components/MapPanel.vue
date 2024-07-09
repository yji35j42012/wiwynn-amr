<style>
.ball{
	position: absolute;
	top: 650px;
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
			<canvas ref="prismCanvas" width="1800" height="1000"></canvas>


			<div class="ball"></div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			pointData: [
				// { x: 100, y: 222, w: 100, h: 20, d: 80, text: '物件1' },
				// { x: 225, y: 204, w: 100, h: 20, d: 80, text: '物件2' },
				// { x: 350, y: 186, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 475, y: 168, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 600, y: 150, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 725, y: 132, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 850, y: 114, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 975, y: 96, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 1100, y: 78, w: 100, h: 20, d: 80, text: '物件3' },
				// { x: 1225, y: 60, w: 100, h: 20, d: 80, text: '物件3' },



				// { x: 180, y: 320, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 490, y: 710, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 615, y: 692, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 740, y: 674, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1365, y: 584, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1490, y: 566, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1615, y: 548, w: 100, h: 20, d: 80, text: '物件1' },

				
				{ x: 535, y: 760, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 660, y: 742, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 785, y: 724, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1410, y: 634, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1535, y: 616, w: 100, h: 20, d: 80, text: '物件1' },
				{ x: 1660, y: 598, w: 100, h: 20, d: 80, text: '物件1' },

			],
		}
	},
	created() {
		for(var i =0; i<10;i++){
			this.pointData.push(
				{x:i*125+100,y:222-18*i,w:100,h:20,d:80,text: '物件1'},
				{x:i*125+180,y:320-18*i,w:100,h:20,d:80,text: '物件1'},
				{x:i*125+410,y:610-18*i,w:100,h:20,d:80,text: '物件1'}
			)
		}
		for(var i =0; i<9;i++){
			this.pointData.push(
				{x:i*125+380,y:400-18*i,w:100,h:20,d:80,text: '物件1'},
				{x:i*125+460,y:498-18*i,w:100,h:20,d:80,text: '物件1'},
			)
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