<script lang="ts">
import { ref, computed } from "vue";
import StarImg from "@/assets/Star.vue";
export default {
  setup() {

    const starCount = ref(5)
    const starColorOutlined = ref('black')
    const starColorFilled = ref('#edaa10')
    const hoverStar = ref(0)
    const currentStar = ref(0)
    const starSize = ref(`${53}px`)
    const fontSize = ref(`${40}px`)
    const fontWeight = ref(500)

    const starArr = computed(() => {
      const resultArr = []
      for (let i = 0; i <= starCount.value; i++)
        if (i !== 0) {
          resultArr.push(i)
        }
      return resultArr
    })

    function setStar(starCount: number) {
      currentStar.value = starCount
    }

    return {
      starCount,
      starColorFilled,
      starColorOutlined,
      starSize,
      fontSize,
      fontWeight,
      starArr,
      hoverStar,
      currentStar,
      setStar
    }
  },
  components: { StarImg }
}

</script>

<template>
  <h3 class="rating" :style="{'fontSize': fontSize, 'font-weight': fontWeight}">Rating</h3>
  <div class="optionsContainer">
    <div class="innerContainer">
      <div class="options">
        <span>Enter star number</span>
        <input v-model="starCount" type="text">
      </div>
      <div class="options">
        <span>Enter the color of selected star</span>
        <input v-model="starColorFilled" type="text">
      </div>
    </div>
    <div class="innerContainer">
      <div class="options">
        <span>Enter the color of unselected star</span>
        <input v-model="starColorOutlined" type="text">
      </div>
      <div class="options">
        <span>Enter the stars size</span>
        <input v-model="starSize" type="text">
      </div>
    </div>
    <div class="options">
      <span>Costomize text</span>
      <input v-model="fontSize" type="text">
      <input v-model="fontWeight" type="text">
    </div>
  </div>
  <div class="wrap">
    <StarImg :fill='hoverStar >= star || currentStar >= star ? starColorFilled : starColorOutlined'
      v-for="star in starArr" :key="star" class="star" :style="{ 'height': starSize }" @mouseover="hoverStar = star"
      @mouseleave="hoverStar = currentStar ? currentStar : 0" @click="setStar(star)" />
  </div>
</template>

<style lang="scss">
input {
  margin: 5px;
  width: 70px;
}

span {
  width: 150px;
}

.optionsContainer {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 0 auto;

  .options {
    margin: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.rating {
  margin-top: 30px;
}

.wrap {
  display: flex;
  justify-content: center;

  .star {
    height: 100px;
    margin: 10px;
    cursor: pointer;
  }
}
</style>