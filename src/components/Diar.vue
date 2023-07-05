<template>
	<div class="wrap">
		<v-container style="width: 100%; max-width: 950px; border: 1px solid black" >

			<Controls :mesic="actualMesic" @zmenamesicu="setNewActualMesic"></Controls>

			<v-row class="myflex">
				<v-col v-for="day in daysOfWeek" :key="day">  {{ day }}
				</v-col>
			</v-row>
			<v-row class="myflex">
				<v-col v-for="day in offsetDayIn1Week" :key="day"/> 
				<v-col v-for="day in daysInMonth" :key="day"> 
					<CardDay  :day="day" :nocni="smeny[this.actualMesic ][day]"> </CardDay>
				</v-col>
			</v-row>
		</v-container>
		<v-list class="konzol">
			<v-list-item>
				today - {{ this.actualMesic }} [ {{ this.today.format('DD MMM  YYYY') }} ]
			</v-list-item>
		</v-list>
	</div>
</template> 



<script>
import moment from "moment";

import CardDay from "./CardDay.vue";
import Controls from './Controls.vue';

const daysOfWeek = moment()._locale._weekdaysShort;

export default {
	props: ['smeny'],
	components: { CardDay, Controls },
	data() {
		return {
			daysOfWeek: daysOfWeek,
			actualMesic : moment().month(),
		}
	},
	computed: {
		today: function(){
			return moment().month(this.actualMesic)
		},
		daysInMonth: function () {
			return this.today.daysInMonth();
		},
		offsetDayIn1Week: function () {
			return this.today.date(1).day()
		},
	},
	methods:{
		setNewActualMesic (cisloMesicu) {
			this.actualMesic = cisloMesicu
		}
	},
	mounted: function () {
		window.data = this.$data; window.vv = this; window.mm = window.moment = moment;
	},
};
</script>







<style scoped>
.konzol>* {
	font-size: 165%;
	margin-bottom:15px;
	font: bold;
}

.wrap {
	width: 100%;
	min-width: 730px;
	border: 1 solid black;
}


.weekdays {
	margin: 0;
	padding: 1rem 0;
	background-color: #dddddd;
	width: 100%;
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: left;
}

.weekdays li {
	display: inline-block;
	flex: 0 0 calc(100% / 7);
	text-align: center;
}

.days {
	margin: 0;
	padding: 1rem 0;
	background-color: #ffffff;
	width: 100%;
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	align-content: flex-start;
}
.myflex{
	display: flex;
	flex-wrap: wrap;
}

.myflex >*{
	display: inline-block;
	padding: 10px;
	flex: 0 0 calc(100% / 7);
	border:1px solid rgb(174, 154, 202);
}

.days li {
	padding: 0.5rem;
	/* border:1px solid grey; */
	list-style: none;
	display: inline-block;
	flex: 0 0 calc(100% / 7);
	text-align: center;
	color: #999;
	font-size: 0.9rem;
	line-height: 1.1rem;
}

</style>