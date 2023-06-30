<template>
    <v-card variant="outlined">
        <v-card-title > {{ this.day  }}</v-card-title>
        <v-card-text>
            <!-- <div>sdsd</div> -->
            <v-btn size="x-small" block   variant="outlined" color="orange"> +</v-btn>
            <v-btn size="x-small" block  variant="outlined" color="indigo-darken-3"> {{ nocni }}</v-btn>
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
    color:rgb(0, 0, 0)
}
.v-card-title{
	padding: 0.5rem  !important;
	color:red !important
}

.v-card-text{
    margin-top: 15px;
    padding: 0 0.7rem !important;
    /* padding: 0.1rem !important; */
}
.v-btn{
   box-shadow: 0 0 5px ;
   margin:3px 0;
   padding: 0px 5px;
   opacity: 0.8;
}
.v-btn:hover{
    opacity: 1;
}
.v-card{
    background-color: rgb(239, 245, 245);
}

</style>