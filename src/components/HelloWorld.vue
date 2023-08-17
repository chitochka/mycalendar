<script setup>


</script>

<template>
<div>
    <v-container style="width:450px;border:1px solid black">
      <v-row class="hlavicka">
        <v-col>Po</v-col>
        <v-col>Ut</v-col>
        <v-col>St</v-col>
        <v-col>Ct</v-col>
        <v-col>Pa</v-col>
        <v-col>So</v-col>
        <v-col>Ne</v-col>
      </v-row>

      <!-- <v-row class="hlavicka">
        <v-col> {{this.rows}} </v-col>
      </v-row> -->

      <v-row v-for="index in 5" :key="index" class="hlavicka">
        
        <v-col   v-for="day in 7" :key="day">  {{index * (0+day)}} </v-col>

      </v-row>

    </v-container>
    <p>
      {{ moment(this.month+"-01-2023", "MM-DD-YYYY") }} <br>{{ this.denNedeli }}
    </p>
</div>
</template>

<script>
import moment from 'moment';

  export default {
    data: () => ({ 
      moment: moment,
      month:5,
    }),
    computed: {
      denNedeli: function () {
        return 4
      // return moment("1-"+this.month+"-2023").day()
      },
      rows : function(){
        return Math.ceil((30 + this.denNedeli)/7)
      }
  }

  } 


</script>

<style scoped>
.hlavicka > *{
  border:1px solid black;
} 
</style>
