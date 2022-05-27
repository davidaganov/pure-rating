<template>
  <div class="wrapper">
    <header class="header">
      <h1 class="title"><strong>Pure</strong> {{ name }}</h1>
    </header>

    <section>
      <!-- First example -->
      <div class="example-wrapper">
        <h2 class="example-title">By default</h2>
        <p class="example-description">Default rating selection</p>
        <RatingSelect name="example" :grade="3"/>
        <RatingSelect name="example" :grade="4"/>
        <RatingSelect name="example" :grade="5"/>
      </div>

      <!-- Second example -->
      <div class="example-wrapper">
        <h2 class="example-title">Custom rating</h2>
        <p class="example-description">Custom colors, size and number of stars</p>
        <RatingSelect name="example" :color="customColor" :size="20" :grade="1" :maxStars="3"/>
        <RatingSelect name="example" :color="customColor" :size="30" :grade="2" :maxStars="4"/>
        <RatingSelect name="example" :color="customColor" :size="40" :grade="3" :maxStars="5"/>
      </div>

      <!-- Third example -->
      <div class="example-wrapper">
        <h2 class="example-title">Counter</h2>
        <p class="example-description">Event for getting a rating</p>

        <div class="example-counter">
          <RatingSelect name="example" @rating="ratingOne = $event"/>
          <span>{{ ratingOne }}</span>
        </div>

        <div class="example-counter">
          <RatingSelect name="example" @rating="ratingSecond = $event"/>
          <span>{{ ratingSecond }}</span>
        </div>

        <div class="example-counter">
          <RatingSelect name="example" @rating="ratingThird = $event"/>
          <span>{{ ratingThird }}</span>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import RatingSelect from "./components/RatingSelect.vue";

export default {
  name: "PureRating",
  components: { RatingSelect },

  data() {
    return {
      name: "Rating",

      ratingOne: NaN,
      ratingSecond: NaN,
      ratingThird: NaN,

      customColor: { star: "tomato", hover: "#f88d8d", empty: "#f8ebeb" }
    };
  }
};
</script>

<style>
.wrapper {
  width: 80%;
  max-width: 1000px;
  margin-left: auto;
  margin-right: auto;
}

.header {
  display: flex;
  align-items: center;
}

.title {
  font: bold 32px "Roboto";
  margin-bottom: 8px;
}
.title strong {
  color: #41b883
}

.example-wrapper {
  margin-top: 40px;
}

.example-wrapper:not(:last-of-type) {
  margin-bottom: 60px;
}

.example-title {
  margin: 0;
}

.example-description {
  margin-top: 10px;
  margin-bottom: 20px;
  color: gray;
}

.example-counter {
  display: flex;
  align-self: center;
}
.example-counter span {
  margin: auto 10px;
  font: normal 18px "Roboto";
}
.example__rating-star {
  /* Reset style */
  background-color: transparent;
  border: 0;
  padding: 0;

  padding: 0 3px;
}

@media (min-width: 769px) {
  .example-title {
    font: bold 26px "Roboto";
  }
  .example-description {
    font: normal 22px "Roboto";
  }
}

@media (max-width: 768px) {
  .example-title {
    font: bold 22px "Roboto";
  }
  .example-description {
    font: normal 16px "Roboto";
  }
}
</style>
