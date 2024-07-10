<template>
	<div :class="['leftpanel', isLeftOpen ? '_open' : '']">
		<button class="normal_btn _report">報表</button>
		<label class="normal_sel">
			<select>
				<option value="1樓">1樓</option>
			</select>
		</label>
		<ul class="leftpanel_group">
			<template v-for="(item, index) in carInfo" :key="index">
				<li :class="['leftpanel_item', item.errorTxt !== '' ? '_error' : '']">
					<div :class="['leftpanel_power', item.powerNum <= 20 ? '_powerLow' : '']" :data-num="item.powerNum">
						<div class="leftpanel_battery">
							<span :style="'width:' + item.powerNum + '%'"></span>
						</div>
					</div>
					<div class="leftpanel_info" data-txt="車號：">{{ item.carNum }}</div>
					<div class="leftpanel_info" data-txt="目的地：">{{ item.dest }}</div>
					<div class="leftpanel_distance">
						<div class="leftpanel_distance_txt">{{ item.destNum }}m</div>
						<div class="leftpanel_distance_line"></div>
						<div class="leftpanel_distance_txt" data-txt="抵達時間：">{{ item.time }}</div>
					</div>
					<div class="leftpanel_info _error" data-txt="異常：" v-if="item.errorTxt !== ''">{{ item.errorTxt }}
					</div>
				</li>
			</template>

		</ul>
		<button :class="['leftpanel_btn', isLeftOpen ? '_open' : '_close']" @click="leftpanel_btn"></button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			isLeftOpen: false,
			carInfo: [
				{ powerNum: 75, carNum: "A0000001", dest: "AA-032", destNum: "321", time: "10:24", errorTxt: "" },
				{ powerNum: 20, carNum: "A0000002", dest: "BB-032", destNum: "200", time: "11:00", errorTxt: "" },
				{ powerNum: 60, carNum: "A0000003", dest: "CC-032", destNum: "500", time: "13:55", errorTxt: "異常原因說明，異常原因說明，異常原因說明。" },
				{ powerNum: 75, carNum: "A0000004", dest: "DD-032", destNum: "568", time: "11:11", errorTxt: "" },
			]
		}
	},
	methods: {
		leftpanel_btn() {
			this.isLeftOpen=!this.isLeftOpen;
			this.$emit('leftpanel-menu', this.isLeftOpen)
		}
	}
};
</script>