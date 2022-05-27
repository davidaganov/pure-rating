<template>
  <div
    class="rating-select"
    :class="name ? `${name}__rating-select` : ''"
    :style="[`height: ${size}px`, colorStar]"
  >
    <div
      class="rating-select__list"
      :class="name ? `${name}__rating-list` : ''"
    >
      <button
        v-for="star in maxStars" :key="star"
        class="star"
        :style="`height: ${size}px`"
        :class="[{ 'star--active': star <= stars }, name ? `${name}__rating-star` : '']"
        type="button"
        @click="rate(star)"
      >

        <svg
          class="star__icon"
          :width="size"
          :height="size"
          :aria-labelledby="`${star} / 5`"
          viewBox="0 0 22 19"
          role="presentation"
        >
          <title lang="en">
            {{ `${star} / 5` }}
          </title>
            <!-- eslint-disable-next-line max-len -->
          <path fill="currentColor" d="M10.1156.67634c.3752-.711147 1.3936-.711147 1.7688-.000001l2.5539 4.840511c.1447.27424.4085.46585.714.51872l5.3928.93308c.7923.13709 1.107 1.10572.5466 1.68232l-3.8144 3.92473c-.2161.2223-.3169.5323-.2727.8393l.779 5.4172c.1145.7958-.7095 1.3945-1.431 1.0397l-4.9114-2.4149c-.2782-.1369-.6042-.1369-.8824 0l-4.91136 2.4149c-.72155.3548-1.54552-.2439-1.43107-1.0397l.77905-5.4172c.04413-.307-.0566-.617-.27271-.8393L.908307 8.65097c-.560396-.57659-.245668-1.54523.546613-1.68232l5.39279-.93308c.30554-.05287.56927-.24448.71396-.51872L10.1156.67634Z"/>
        </svg>

      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    grade: { type: Number, default: 5 },
    maxStars: { type: Number, default: 5 },
    size: { type: Number, default: 25 },
    name: { type: String, default: undefined },

    color: {
      type: Object,
      default: () => ({
        empty: "", star: "", hover: "", focus: ""
      })
    }
  },

  emits: ["rating"],

  data() {
    return { starsValue: this.grade };
  },

  computed: {
    stars: {
      get() {
        this.$emit("rating", this.starsValue);
        return this.starsValue;
      },
      set(newValue) { this.starsValue = newValue; }
    },

    colorStar() {
      return {
        "--star-empty": this.color.empty ? this.color.empty : "#D2D8D6",
        "--star-color": this.color.star ? this.color.star : "#FFD55B",
        "--star-hover": this.color.hover ? this.color.hover : "#EAD695",
        "--star-focus": this.color.focus ? this.color.focus : "blue"
      };
    }
  },

  methods: {
    rate(star) {
      if (typeof star === "number" && star <= this.maxStars && star >= 0) {
        this.stars = this.stars === star ? star - 1 : star;
      }
    }
  }
};
</script>

<style>
@import "../assets/default.css";
</style>
