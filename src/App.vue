<script lang="ts">
import { defineComponent } from "vue";
import SlavaStar from "./components/SlavaStar.vue";
import StarRating from "./components/StarRating2.vue";

export default defineComponent({
  components: {
    StarRating,
    SlavaStar
  },
});
</script>

<template>
  <div>
    <StarRating :rating="3" />
  </div>
  <div>
    <SlavaStar />
  </div>
</template>

<style scoped>

</style>
