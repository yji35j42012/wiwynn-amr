<template>
	<div class="mappanel">
		<div id="mappanel_box" class="mappanel_box">
			<div class="mappanel_box_row">
				<div v-for="(index) in 10" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<!-- style="top: 100px;left: 50px" -->
			<div class="mappanel_box_row" style="top: 0px; padding-left: 50px; display: none1;">
				<div v-for="(index) in 10" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>

			<!-- style="top: 200px;left: 100px" -->
			<div class="mappanel_box_row" style="top: 200px; padding-left: 100px; display: none;">
				<div v-for="(index) in 5" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 50 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<!-- <div class="rode"></div>
			<div class="rode"></div> -->
		</div>


		<canvas id="mycanvas" class="mappanel_box_canvas" width="1000" height="700"></canvas>
	</div>
</template>

<script>
export default {
	data() {
		return {
			pointData: [
				{ x1: 900, y1: 100, x2: 80, y2: 75, text: '巡邏點1' },
				{ x1: 80, y1: 75, x2: 200, y2: 300, text: '巡邏點2' },
				{ x1: 200, y1: 300, x2: 580, y2: 500, text: '巡邏點3' },
				{ x1: 580, y1: 500, x2: 900, y2: 100, text: '巡邏點4' },
			]
		}
	},
	created() {
		this.doDraw();
	},
	mounted() {
		let cw=document.querySelectorAll('#mappanel_box .mappanel_box_row:nth-child(1) > .side');

		console.log('cw',cw);
		// let mappanel_box_h=document.getElementById('mappanel_box');
		// let canvas=document.getElementById('mycanvas');
		// canvas.style=`width:${ mappanel_box[0].offsetWidth }px; height:${ mappanel_box_h.offsetHeight }px;`
		// console.log('w', mappanel_box[0].offsetWidth);
		// console.log('w', mappanel_box[0].offsetHeight);
	},
	methods: {
		doDraw() {
			let canvas=document.getElementById('mycanvas');
			let a=setInterval(() => {
				canvas=document.getElementById('mycanvas');
				if (!canvas) {
					return false;
				} else {
					clearInterval(a);
					let context=canvas.getContext('2d');
					this.clearCanvas(context, canvas);
					this.pointData.forEach((item) => {
						const { x1, y1, x2, y2, text }=item

						context.lineWidth=3;
						context.lineCap='round';
						context.strokeSytle='#fff';
						context.fillStyle='rgb(0,255,255)';
						context.beginPath();

						// context.shadowColor='rgb(20,20,235)';
						// context.shadowOffsetX=0;
						// context.shadowOffsetY=0
						// context.shadowBlur=6;

						// context.setLineDash([5, 10]);

						context.moveTo(x1, y1);
						context.lineTo(x2, y2);

						context.stroke();
					})
				}
			})
		},
		clearCanvas(ctx, canvas) {
			ctx.clearRect(0, 0, canvas.width, canvas.height);
		}
	}
};
</script>