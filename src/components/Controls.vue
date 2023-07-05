<template>
	<v-row class="control">
		<v-col class="text-right" align-self="center">
			<!-- <v-btn append-icon="mdi-arrow-left-bold" variant="outlined" :disabled="!this.month" @click="this.select.index = this.month-1">
						 {{ this.month!==0? nazvyMesicu[this.month-1]:nazvyMesicu[11]  }} 
					</v-btn> -->
		</v-col>
		<v-col align-self="center">
			<v-select density="compact" variant="outlined" label="Mesic" return-object @update:modelValue="zmena"
				:items="allMesice" v-model="select">
			</v-select>
		</v-col>
		<v-col align-self="center">
			<!-- <v-btn prepend-icon="mdi-arrow-right-bold" variant="outlined" @click="this.month++">Next</v-btn> -->
		</v-col>
	</v-row>
	<v-row>		<v-col>		</v-col>	</v-row>
</template>


<script>
import moment from "moment";
const allMesice = moment()._locale._months;

export default {
	props: ['mesic'],
	emits: ['zmenamesicu'],
	data: (vm) => 	({
		allMesice: allMesice,
		select: allMesice[ vm.mesic ]
	}),
	methods: {
		zmena(mesic) {
			this.$emit('zmenamesicu', this.allMesice.indexOf(mesic))
		}
	}
}
</script>