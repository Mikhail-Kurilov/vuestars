<script lang="ts">
import { ref, computed, watch } from "vue";
// import StarImg from "@/assets/Star.vue";
export default {
  setup() {

    const starCount = ref(5)

    const starColorOutlined = ref('#fff')
    const starColorFilled = ref('#edaa10')

    const starArr = computed(() => {
      const resultArr = []
      for (let i = 0; i <= starCount.value; i++)
        if (i !== 0) {
          resultArr.push(i)
        }
      return resultArr
    })

    const hoverStar = ref(0)
    const currentStar = ref(0)

    function setStar(starCount: number) {
      currentStar.value = starCount
    }

    return {
      starCount,
      starColorFilled,
      starColorOutlined,
      starArr,
      hoverStar,
      currentStar,
      setStar
    }
  },
  // components: { StarImg }
}

</script>

<template>
  <span>Enter star count</span>
  <input v-model="starCount" type="text">
  <span>Enter color set star</span>
  <input v-model="starColorFilled" type="text">
  <span>Enter color empty star</span>
  <input v-model="starColorOutlined" type="text">
  <h3>Rating</h3>
  <div class="wrap">
    <div v-for="star in starArr" :key="star" class="star"
      :style="{ 'background-color': hoverStar >= star || currentStar >= star ? starColorFilled : starColorOutlined }"
      @mouseover="hoverStar = star" @mouseleave="hoverStar = star === 1 ? 0 : star" @click="setStar(star)" />
  </div>
</template>

<style lang="scss">
.wrap {
  display: flex;

  .star {
    width: 100px;
    height: 100px;
    margin: 10px;
    border: 2px solid black
  }
}
</style>