<template>
  <div class="home">
    <Header/>
    <main v-if="!loading">
      <data-title :text="title" :dataDate="dataDate"/>
      <data-boxes :stats="stats"/>
      <country-select :countries="countries" @get-country="getCountryData"/>
      <button v-if="showbutton" @click="resetData" class="text-xl m-5 bg-red-300 p-3 rounded">Clear Country</button>
    </main>
    <main v-else class="flex flex-col align-center justify-center text-center">
      <img :src="loadingImg" class="w-24 m-auto" alt="">
    </main>
  </div>
</template>

<script>

import Header from '../components/Header.vue'

import DataTitle from '../components/DataTitle.vue'
import DataBoxes from '../components/DataBoxes.vue'
import LoginVue from '../../../vueNew/src/components/Login.vue'
import CountrySelect from '../components/CountrySelect.vue'

export default {
  name: 'Home',
  data(){
    return{
      loading:true,
      countries:[],
      title:'Global',
      dataDate:'',
      stats:{},
      loadingImg: require('../assets/loading-gif.gif'),
      showbutton:false
    }
  },
    
  components: {
    Header,
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  async created(){
    
    
    const data = await this.getData()
    console.log(data);
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  },
  methods:{
    async getData(){
      
      const resp = await fetch('https://api.covid19api.com/summary')
      const data = await resp.json()
      return data
      
    },

    getCountryData(country){
      this.title = country.Country
      this.stats = country
      this.showbutton = true
    },

    async resetData(){
      this.loading = true
      const resetData = await this.getData()
      this.stats = resetData.Global
      this.title = 'Global'
      this.showbutton = false
      this.loading = false
    }
  }
}
</script>
