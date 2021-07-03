<template>
    <div class="flex text-xl justify-center">
       <div class="grid md:grid-cols-2 gap-4">
           <div class="confired bg-blue-100 text-center p-10 rounded">
                <h3>Cases</h3>
                <div class="mb-4">
                    Total Confirmed: {{ stats.TotalConfirmed }}
                </div>
                <div class="text-2xl mb-4">
                    New Confirmed: {{ stats.NewConfirmed }}
                </div>
                
           </div>
           <div class="confired bg-blue-200 text-center p-10 rounded">
                <h3>Deaths</h3>
                <div class="text-2xl mb-4">
                    Total Deaths: {{ stats.TotalDeaths }}
                </div>
                <div class="text-2xl mb-4">
                    New Deaths: {{ stats.NewDeaths }}
                </div>
                
           </div>
       </div>
    </div>
</template>

<script>
export default {
    name:'DataBoxes',
    props:['stats']
}
</script>