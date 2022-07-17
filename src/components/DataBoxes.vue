<template>
  <div class="grid md:grid-cols-2 gap-4">
    <div class="bg-blue-100 p-10 text-center rounded shadow-md">
      <h3 class="text-3xl font-bold text-blue-900 mb-5">Cases:</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ numberWithCommas(stats.NewConfirmed) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ numberWithCommas(stats.TotalConfirmed) }}
        <!--   {{ stats }} -->
      </div>
    </div>
    <div class="bg-blue-300 p-10 text-center rounded shadow-md">
      <h3 class="text-3xl font-bold text-blue-900 mb-5">Deaths:</h3>
      <div class="text-2xl mb-4">
        <span class="font-bold">New:</span>
        {{ numberWithCommas(stats.NewDeaths) }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Total:</span>
        {{ numberWithCommas(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["stats"],
  name: "DataBoxes",
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
