<template>
  <div>
    <h2 class="text-3xl md:text-5xl text-center font-bold">{{ text }}</h2>
    <div class="text-2xl mb-10 mt-5 text-center">
      {{ timeFormat }}
    </div>
  </div>
</template>
<script>
import moment from "moment";
export default {
  name: "DataTitel",
  props: ["dataDate", "text"],
  computed: {
    timeFormat() {
      return moment(this.dataDate).format("MMMM Do YYYY, hh:mm:ss a");
    },
  },
};
</script>
