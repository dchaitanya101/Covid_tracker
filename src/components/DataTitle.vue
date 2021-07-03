<template>
    <div class="text-center  bg-gray-300">
        <div class="sm:text-2xl md:text-4xl font-bold m-5">{{ text }}</div>
        <div class="sm:text-xl md:text-2xl m-4">
            {{ timestamp }}
        </div>
    </div>
</template>

<script>
import moment from 'moment'
export default {
    name:'DataTitle',
    props:['text','dataDate'],
    computed:{
        timestamp: function(){
            return moment(this.dataDate).format('MMMM Do YYYY, HH:mm:ss a')
        }
    }
}
</script>