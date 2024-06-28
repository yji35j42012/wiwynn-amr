<template>
	<div class="mappanel">
		<div id="mappanel_box" class="mappanel_box" style="padding-top:200px;">
			<div class="mappanel_box_row">
				<div v-for="(index) in count" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<!-- <div class="mappanel_box_row" style="padding-left: 50px;">
				<div v-for="(index) in count" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<div class="mappanel_box_row" style="padding-left: 100px;">
				<div v-for="(index) in count" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<div class="mappanel_box_row" style="padding-left: 150px;">
				<div v-for="(index) in count" :key="index" class="side"
					:style="'transform: rotateX(-30deg) rotateY(290deg) translateX(0px) translateY(' + index * 0 + 'px);left:' + (index) * 0 + 'px;top:' + index * -20 + 'px;'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<div class="mappanel_box_row" style="padding-left: 200px;">
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-20px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-40px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-60px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-80px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<div class="mappanel_box_row" style="padding-left: 250px;">
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-20px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-40px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-60px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-80px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div>
			<div class="mappanel_box_row" style="padding-left: 300px;">
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-20px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-40px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-60px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
				<div class="side" :style="'transform: rotateX(-30deg) rotateY(290deg); top:-80px'">
					<div class="side_box _top"></div>
					<div class="side_box _left"></div>
					<div class="side_box _right"></div>
				</div>
			</div> -->
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
			],
			count: 1
		}
	},
	created() {
		this.doDraw();
	},
	mounted() {
		let mappanel_box_h=document.getElementById('mappanel_box');
		let canvas=document.getElementById('mycanvas');
		canvas.style=`width:${ this.count*115 }px; height:${ mappanel_box_h.offsetHeight }px;`
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

						context.beginPath();
						context.lineWidth=3;
						context.lineCap='round';
						context.strokeStyle="white";

						// context.shadowColor='#EFEFEF';
						context.shadowColor='#EFEFEF';
						context.shadowOffsetX=0;
						context.shadowOffsetY=0;
						context.shadowBlur=1;

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