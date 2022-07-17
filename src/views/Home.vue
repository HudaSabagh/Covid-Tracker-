<template>
  <main v-if="!loading" class="text-3xl">
    <DataTitel :text="title" :dataDate="dataDate" />
    <DataBoxes :stats="stats" />
    <Countries @get-country="getCountryData" :countries="countries" />
    <div class="flex items-center justify-center">
      <button
        v-if="stats.ID"
        @click="clearCountry"
        class="bg-red-700 focus:outline-none hover:bg-red-900 rounded mt-10 p-3 text-white"
      >
        Clear Country
      </button>
    </div>
  </main>
  <main v-else class="flex flex-col justify-center align-center text-center">
    <div class="text-3xl md:text-5xl mb-5">Fetching</div>
    <img
      :src="loadImage"
      alt="loading"
      class="w-24 m-auto rounded shadow-2xl border-2"
    />
  </main>
</template>

<script>
import axios from "axios";
import DataTitel from "../components/DataTitle.vue";
import DataBoxes from "../components/DataBoxes.vue";
import Countries from "../components/Countries.vue";
// @ is an alias to /src

export default {
  name: "Home",
  components: {
    DataTitel,
    DataBoxes,
    Countries,
  },
  data() {
    return {
      loading: true,
      dataDate: "",
      title: "Global",
      countries: [],
      stats: {},
      loadImage: require("../assets/1amw.gif"),
      data: null,
    };
  },
  methods: {
    /*   async getCovidData() {
      const res = await fetch(`https://api.covid19api.com/summary`);
      const data = await res.json();
      return data;
    }, */
    async getCovidData() {
      return axios
        .get(`https://api.covid19api.com/summary`)
        .then((res) => (this.data = res.data));
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountry() {
      this.loading = true;
      const data = await this.getCovidData();
      this.stats = data.Global;
      this.title = "Global";
      this.loading = false;
    },
  },
  async created() {
    const data = await this.getCovidData();
    console.log(data);
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
