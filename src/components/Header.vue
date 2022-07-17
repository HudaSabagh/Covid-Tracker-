<template>
  <header class="bg-blue-900 p-3 text-white text-center mb-10">
    <div class="text-3xl md:text-5xl font-bold mb-3">
      <i class="fa-solid fa-viruses"></i> Covid-Tracker
    </div>
    <p>
      ApI by
      <a
        class="text-blue-300"
        href=" https://api.covidtracking.com/v1/status.json"
        target="_blank"
      >
      api.covidtracking</a
      >
    </p>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>
