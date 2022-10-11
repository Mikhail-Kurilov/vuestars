<template>
  <div class="Star-rating">
    <!-- first span contain stars without fill color -->
    <span v-for="index in starNumber" :key="index" class="Star Star--outlined"></span>
    <!-- colored stars renders above outlined, width changes inside style flag -->
    <div class="Star-rating--colored" :style="ratingWidthStyle">
      <span v-for="index in starNumber" :key="index" class="Star Star--colored"></span>
    </div>
  </div>
</template>
<script lang="ts">

export default {
  name: "StarRating",
  props: {
    rating: {
      type: Number,
      default: 0,
    },
    starNumber: {
      type: Number,
      default: 5,
    }
  },
  computed: {
    ratingWIdth() {
      return this.rating / this.starNumber * 100
    },
    ratingWidthStyle() {
      return `width: ${this.ratingWIdth}%`
    }
  }
}
</script>
<style lang="scss" scoped>
.Star-rating {
  position: relative;
  display: inline-flex;

  &--colored {
    display: inline-flex;
    position: absolute;
    width: 0;
    height: 100%;
    top: 0;
    left: 0;
    overflow: hidden;
  }
}

.Star {
  display: inline-block;
  flex-shrink: 0;
  width: 53px;
  height: 53px;

  &--colored {
    background: url('./../../img/star__filled.svg') center no-repeat;
  }

  &--outlined {
    background: url('./../../img/star__outlined.svg') center no-repeat;
  }
}
</style>