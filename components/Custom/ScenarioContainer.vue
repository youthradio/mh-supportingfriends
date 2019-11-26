<template>
  <div class="Container">
    <div class="bigImageContainer">
      <img :src="require(`~/assets/images/${scenario.img.trim()}`)" class="bigImage">
      <div class="textContent">
        {{ scenario.text }}
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="(option, id) in scenario.options"
        :key="option"
        @click="processOption(id)"
        class="bigImageContainer"
      >
        <img :src="require(`~/assets/images/${option.img.trim()}`)" class="bigImage">
        <div class="textContent">
          {{ option.option }}
        </div>
      </div>
    </div>

    <div
      v-if="clickedElement"
      class="flex-container"
    >
      <div
        v-for="(result, id) in scenario.options"
        :key="result"
        :class="['optionContainer', selectedOption > -1 ? (selectedOption === id ? 'selectedResult':'nonResult'):'']"
      >
        <h5>Results:</h5>
        <div class="textContent">
          {{ result.result }}
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
      clickedElement: false,
      selectedOption: -1
    }
  },
  methods: {
    processOption (id) {
      console.log(id)
      this.clickedElement = true
      this.selectedOption = id
    }
  }
}
</script>
  <style scoped lang="scss">
@import "~@/css/vars";
@import "~@/css/base";
.flex-container {
  display: flex;
  padding-top: 10px;
  justify-content: center;
  /* bigImageContainer is reused outside of flex so this wouldn't apply to anything outside of a flexbox anyway */
  .bigImageContainer {
    flex-basis: 50%;
  }
  .optionContainer {
    flex-basis: 50%;
    h5 {
      padding: 10px;
    }
  }
}

.selectedResult {
  background-color: red;
}
.nonResult {
  background-color: blue;
}

.optionContainer {
  color: grey;
}

.correct-result {
  color: $green;
}

.bigImageContainer {
  position: relative;
}
.bigImage {
  z-index: -1;
  // position: absolute;
  /* make image size based on the parent container, which is dependent on text */
  height: auto;
  width: 100%;
  max-height: 300px;
  /* clean stretching */
  object-fit: cover;
  object-position: center;
}
.textContent {
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
