<template>
  <div class="p-8 flex-grow">
    <div>
      <p class="text-gray-400">Dashboard ></p>
    </div>
    <div class="mt-6 relative">
      <svg
        v-if="search == ''"
        style="width: 24px; height: 24px"
        class="absolute top-2.5 left-1.5"
        viewBox="0 0 24 24"
      >
        <path
          fill="currentColor"
          d="M9.5,3A6.5,6.5 0 0,1 16,9.5C16,11.11 15.41,12.59 14.44,13.73L14.71,14H15.5L20.5,19L19,20.5L14,15.5V14.71L13.73,14.44C12.59,15.41 11.11,16 9.5,16A6.5,6.5 0 0,1 3,9.5A6.5,6.5 0 0,1 9.5,3M9.5,5C7,5 5,7 5,9.5C5,12 7,14 9.5,14C12,14 14,12 14,9.5C14,7 12,5 9.5,5Z"
        />
      </svg>
      <input type="text" class="border w-4/6 sm:w-4/5 p-2" v-model="search" />
      <button
        type="submit"
        @click="searchByCountry"
        class="p-2 -m-1.5 bg-blue-500 text-white"
        :disabled="search == ''"
      >
        Search
      </button>
    </div>
    <section class="text-center mt-5" v-if="countryData.length !== 0">
      <h2 class="mb-3 text-2xl md:text-3xl font-bold">
        {{ countryData.country + ' (' + countryData.continent + ')' }}
      </h2>
      <div class="flex justify-content flex-col sm:flex-row gap-y-6 flex-wrap">
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Today Cases</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.todayCases }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Today Deaths</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.todayDeaths }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Total Cases</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.cases }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Active Cases</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.active }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Total Deaths</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.deaths }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Total Tests</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.tests }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Total Recovered</h2>
          <p class="text-2xl md:text-3xl">{{ countryData.recovered }}</p>
        </div>
        <div class="sm:w-2/4">
          <h2 class="font-extralight uppercase text-lg md:text-xl">Total Vaccinated</h2>
          <p class="text-2xl md:text-3xl">
            {{conutryVaccine[Object.keys(conutryVaccine)[0]] }}
          </p>
          </p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Tracker',
  data() {
    return {
      search: '',
      countryData: [],
      conutryVaccine: [],
    }
  },
  methods: {
    async searchByCountry() {
      let data = await this.$axios.$get(
        `https://disease.sh/v3/covid-19/countries/${this.search}`
      )
      this.countryData = data
      let totalVaccinted = await this.$axios.$get(
        `https://disease.sh/v3/covid-19/vaccine/coverage/countries/${this.search}?lastdays=1`
      )
      this.conutryVaccine = totalVaccinted.timeline
    },
  },
}
</script>
