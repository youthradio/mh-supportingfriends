<template>
  <div class="container">
    <h4>
      {{ scenario.title }}
    </h4>
    <div class="position-relative">
      <img
        :src="require(`~/assets/images/${scenario.img.trim()}`)"
        class="bigImage"
      >
      <div class="textContent">
        {{ scenario.text }}
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="(option, id) in scenario.options"
        :key="`${option}-${id}`"
        :class="['basis-50','position-relative','pointer', (id === 0 ? 'meanResponse' : 'niceResponse')]"
        @click="processOption(id)"
      >
        <img
          :src="require(`~/assets/images/${option.img.trim()}`)"
          class="bigImage"
        >
        <div class="textContent">
          {{ option.option }}
        </div>
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="(option, id) in scenario.options"
        :key="`${option}-${id}`"
        class="basis-50"
      >
        <div
          v-if="selectedOption > -1"
          :class="['optionContainer', selectedOption === id ? 'selectedResult':'nonResult']"
        >
          <h5>Results:</h5>
          <p>
            {{ option.result }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  components: {
  },
  props: {
    scenario: {
      type: Object,
      required: true,
      default: null
    }
  },
  data () {
    return {
      intIndex: 0,
      clickedElement: false,
      selectedOption: -1
    }
  },
  methods: {
    processOption (id) {
      this.clickedElement = true
      this.selectedOption = id
    },
    nextQuestion () {
      this.intIndex = this.intIndex + 1
    }
  }
}
</script>
  <style scoped lang="scss">
@import "~@/css/vars";
@import "~@/css/base";

.flex-container {
  display: flex;
  justify-content: center;
  /* bigImageContainer is reused outside of flex so this wouldn't apply to anything outside of a flexbox anyway */
  .basis-50 {
    flex-basis: 50%;
    margin-top: 1rem;
  }
  .basis-50:first-of-type {
    margin-right: 1rem;
  }
  .optionContainer {
  }
}
.pointer {
  cursor: pointer;
}
.meanResponse:hover {
  background-color: red;
}
.niceResponse:hover {
  background-color: yellow;
}

.selectedResult {
  h5 {
    color: $green;
  }
  .textContent {
    color: $black;
  }
}
.nonResult {
  h5 {
    color: $red;
  }
  .textContent {
    color: $red;
  }
}

.optionContainer {
  color: grey;
}

.correct-result {
  color: $green;
}

.position-relative {
  position: relative;
}
.bigImage {
  z-index: -1;
  position: absolute;
  height: 100%;
  width: 100%;
  object-fit: cover;
  object-position: center;
}
.textContent {
  @media screen and (min-width: 450px) {
    min-height: 250px;
  }
}
</style>
