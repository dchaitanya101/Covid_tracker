<template>
    <div class="m-5">
        <select @change="valueSelected" v-model="selected" class="form-select mt-10 block text-2xl border p-3 bg-gray-200 rounded">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :key="country.ID" :value="country.ID">{{ country.Country }}</option>
        </select>
    </div>
</template>

<script>
export default {
    name:'CountrySelect',
    props:['countries'],
    data(){
        return {
            selected:0
        }
    },
    methods:{
        valueSelected(){
            const country = this.countries.find((item) => item.ID === this.selected)
            console.log(country);
            this.$emit('get-country', country)
        }
    }
}
</script>