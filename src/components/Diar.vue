<template>
	<!-- <div> -->
		<div class="wrap">
		<v-container style="width: 100%; max-width: 950px; border: 1px solid black">
			<v-row class="control">
				<v-col class="text-right" align-self="center">
					<v-btn append-icon="mdi-arrow-left-bold" variant="outlined" :disabled="!this.month" @click="this.select.index = this.month-1">
						 {{ this.month!==0? nazvyMesicu[this.month-1]:nazvyMesicu[11]  }} 
					</v-btn>
				</v-col>
				<v-col  align-self="center">
					<!-- <h2>{{ this.date.format('MMMM') }}</h2> -->
					<v-select  density="compact"  variant="outlined" label="Mesic" return-object v-model="select" :items="selectItems"
						:item-title="'text'" :item-text="'text'" :item-value="'index'">
					</v-select>
				</v-col>
				<v-col  align-self="center">
					<v-btn prepend-icon="mdi-arrow-right-bold" variant="outlined" @click="this.month++">Next</v-btn>
				</v-col>
			</v-row>
			<v-row>
				<v-col>
					<div id="month-calendar">
						<ul class="weekdays">
							<li v-for="item in this.listOfDays" :key="item">{{ item }}</li>
						</ul>

						<ul class="days">
							<li v-for="n in this.denNedeli" :key="n"></li>
							<li v-for="day in this.daysInMonth" :key="day">
								<CardDay :day="day" :nocni="smeny[this.month ][day]"> </CardDay>
								<!-- {{ n }} -->
							</li>
						</ul>
					</div>
				</v-col>
			</v-row>
		</v-container>
		<v-container >
		<v-layout row wrap align-center>
			<v-flex class="mr-5" xs2>
				this.month ={{ this.month }}

			</v-flex>
		<v-flex xs2>
			this.select = {{ this.select  }}
		</v-flex>
		</v-layout>
		</v-container>

	</div>
</template> 



<script>
import "moment/locale/ru.js";
import moment from "moment";
moment.locale('ru')


import CardDay from "./CardDay.vue";



export default {
    props: ['smeny'],
    components: { CardDay },
	data () {
      return {
        listOfDays: [],
        select: {index:null},
        selectItems:  moment()._locale._months.map(function (text, index) {return {index, text}}),
		nazvyMesicu : moment()._locale._months,
	}
	},
    computed: {
        date: function () {
            return moment(this.month + "-01-2023");
        },
        daysInMonth: function () {
            return this.date.daysInMonth();
        },
        denNedeli: function () {
            return this.date.day();
        },
		month : function(){
			if (this.select.index===null) this.select={index:moment().month()}
			return this.select.index
		}
    },
    mounted: function () {
        this.listOfDays = moment()._locale._weekdaysShort;
		this.select = this.selectItems[moment().month()]


        // console.log(this.date.format("DD-MMYYYY"));
		// console.log('\nnazvy MEsicu= ', this.selectItems ,"")
		// console.log('select2 = ', this.select )
		// console.log('month = ', this.month )
		window.data = this.$data; window.vv =this; window.mm = window.moment = moment;
    },
};
</script>







<style scoped>
.wrap {
    width: 100%;
	min-width: 730px;
    border: 1 solid black;
}


/* .control button{} */

/* месяцы и годы */
#month-calendar {
    width: 100%;

    /* height: 100%; */
}

.month {
    margin: 0;
    padding: 3rem 2rem 2rem;
    background: #555555;
    text-align: center;
    width: 100%;
    color: #ffffff;
    list-style: none;
}

.month li {
    padding: 0;
    margin: 0;
    font-size: 1.5rem;
    line-height: 1.4;
    letter-spacing: 0.1rem;
    text-transform: uppercase;
    font-weight: 700;
}



.month li.prev,
.month li.next {
    cursor: pointer;
}

.month li.prev {
    float: left;
}

.month li.next {
    float: right;
}

/* дни недели */
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

/* дни */
.days {
    margin: 0;
    padding: 1rem 0;
    background-color: #ffffff;
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: left;
    align-content: flex-start;
    /* height: 14rem; */
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

.days li.date-now {
    color: #000;
    font-weight: 700;
}
</style>