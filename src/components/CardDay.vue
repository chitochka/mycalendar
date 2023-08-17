<template>
    <v-card variant="outlined">
        <v-card-title > {{ this.day  }}</v-card-title>
        <v-card-text>
            <!-- <div>sdsd</div> -->
            <v-btn class="btn-den" size="x-small" block   variant="outlined" color="orange"> +</v-btn>
            <v-btn class="btn-noc" size="x-small" block  variant="outlined" color="indigo-darken-3"> {{ nocni }}</v-btn>
        </v-card-text>
    </v-card>


</template>



<script>
// import { defineComponent } from '@vue/composition-api'

export default {
    props:['day','nocni'],
    data: () => ({

    })
}

</script>
<style scope>
.v-card-title {
    font-size: 130%;
    background-color: rgb(191, 199, 199);
    /* color:rgb(0, 0, 0) */
}
.v-card-title{
	padding: 0.5rem  !important;
	color:red !important;
    /* position: absolute; */
    padding: 0px !important;
    text-align: center;
    top:3px;
    color: #555 !important;;
    background: none;

}


.v-btn{
   box-shadow: 0 0 5px ;
   margin:3px 0;
   padding: 0px 5px;
   opacity: 0.9;
}
.v-btn:hover{
    opacity: 1;
}
div.v-card{
    /* background-color: rgb(169, 88, 245); */
    border: 1px dotted #888;
    box-shadow: 0px 0px 5px 3px rgb(235,235,235);
}

div.v-card .v-card-text{
    margin-top: 8px;
    /* margin-left: 5px;; */
    padding: 0 0.15rem !important;
 
    /* padding: 0.1rem !important; */
}

div.v-card .v-card-text > .btn{
    font-weight: 800;
    font-size: 125%;
    padding: 110px 5px !important;
}

.v-card  .v-card-text .btn-den{
    margin-bottom: 0px;
    background: rgb(217, 219, 58) !important;
    border-radius: 5px 5px 0px 0px;
}

div.v-card  .v-card-text .btn-noc{
    color: rgb(255, 255, 7) !important;

    margin-top: 0px;
    background: #3636e7;
    border-radius: 0px 0px 5px 5px;
}




</style>