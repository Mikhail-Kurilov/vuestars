<script lang="ts">
import { defineComponent } from "vue";
import MainStar from "./components/MainStar.vue";
//import StarRating from "./components/StarRating2.vue";

export default defineComponent({
  components: {
    // StarRating,
    MainStar
  },
});
</script>

<template>
  <div>
    <!--<StarRating :rating="3" />-->
  </div>
  <div>
    <MainStar />
  </div>
</template>

<style scoped>

</style>
