<template>
  <div>
    <select
      @change="changeCountry()"
      v-model="selected"
      class="form-select w-full rounded border mt-10 p-3 focus:outline-none font-light text-2xl md:text-3xl"
    >
      <!-- from-blue-600 to-purple-500 bg-gradient-to-r w-full h-64 block  to make bg graidient-->
      <option value="0">Choose Country:</option>
      <option
        v-for="country in countries"
        :value="country.ID"
        :key="country.ID"
      >
        {{ country.Country }}
      </option>
    </select>
  </div>
</template>
<script>
export default {
  name: "Countries",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    changeCountry() {
      const country = this.countries.find((item) => item.ID === this.selected);
      console.log(country);
      this.$emit("get-country", country);
    },
  },
};
</script>
