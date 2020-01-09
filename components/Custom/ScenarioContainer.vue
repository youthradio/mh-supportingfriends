<template>
  <div class="container">
    <h4>
      {{ scenario.title }}
    </h4>
    <div class="position-relative scenario-container">
      <div class="textContent">
        {{ scenario.text }}
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="(option, id) in scenarioOptions"
        :key="`${option}-${id}`"
        :class="['basis-50 position-relative btm-left-in pointer round talk-bubble', selectedOptionClass(option, id)]"
        @click="processOption(option, id)"
      >
        <div class="textContent">
          {{ option.option }}
        </div>
      </div>
    </div>
    <div class="flex-container">
      <div
        v-for="(option, id) in scenarioOptions"
        :ref="`option-id-${id}`"
        :key="`${option}-${id}`"
        class="basis-50"
      >
        <div
          v-if="selectedOptionId > -1"
          :class="['optionContainer', (option.iscorrect.trim() === 'true' ? 'selectedResult':'nonResult')]"
        >
          <h5>Result</h5>
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
      selectedOptionId: -1
    }
  },
  computed: {
    scenarioOptions () {
      return this.scenario.options
        .slice(0)
        .sort(() => 0.5 - Math.random())
    }
  },
  methods: {
    selectedOptionClass (option, id) {
      if (this.selectedOptionId > -1) {
        // if (this.selectedOptionId === id) {
        if (option.iscorrect.trim() === 'true') {
          return 'happySun'
        } else {
          return 'sadSun'
        }
      }
      return ''
    },
    processOption (option, id) {
      this.clickedElement = true
      this.selectedOptionId = id
      this.$refs[`option-id-${id}`][0].scrollIntoView({ behavior: 'smooth', block: 'center' })
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
@import "~@/css/mixins";

.flex-container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  /* bigImageContainer is reused outside of flex so this wouldn't apply to anything outside of a flexbox anyway */
  .basis-50 {
    flex-basis: 50%;
    margin-top: 1rem;
  }
  .basis-50:first-of-type {
    margin-right: 1rem;
  }
  @include breakpoint(medium) {
    flex-direction: row;
  }
}

.scenario-container {
  background-color: #efefef; //temporary
  border: 8px solid #5c9fb5;
  border-radius: 3rem;
  .textContent {
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;
    text-align: center;
    margin: 0 2rem 0 2rem;
  }
  margin: 1rem 0 1rem 0;
}

.happySun:after {
  content: "";
  background: url("~assets/images/sun-wake.png") no-repeat;
  position: absolute;
  overflow: hidden;
  width: 80px; // these may have to be pixels!
  height: 80px;
  right: -1.5rem;
  @include breakpoint(medium) {
    top: 12rem;
    right: -1rem;
  }
}
.sadSun:after {
  content: "";
  background: url("~assets/images/sad-wake.png") no-repeat;
  position: absolute;
  overflow: hidden;
  width: 120px; // these may have to be pixels!
  height: 120px;
  top: -60.5px;
  right: 0rem;
  left: -3.5rem;
  @include breakpoint(medium) {
    top: -60.5px;
    left: -2.5rem;
  }
}

.pointer {
  cursor: pointer;
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
  opacity: 0.3;
  h5 {
    color: $red;
  }
  .textContent {
    color: $red;
  }
}

.optionContainer {
  color: grey;
  h5 {
    padding: 0;
  }
}

.correct-result {
  color: $green;
}

.position-relative {
  position: relative;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
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
  padding: 0.5rem;
  @media screen and (min-width: 450px) {
    min-height: 10rem;
  }
}

.talk-bubble {
  display: inline-block;
  position: relative;
  height: auto;
  background-color: #5c9fb5;

  margin: 1rem 1rem 3rem 1rem;
  padding: 1rem;
  border-radius: 30px;
  border-color: grey;
  .textContent {
    background-color: #5c9fb5;
    color: #efefef;
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;
  }
  .textContent:hover {
    background-color: #5c9fb5;
  }
}
.round {
  border-radius: 30px;
}

/*Right triangle, placed bottom left side slightly in*/
.btm-left-in:before {
  content: " ";
  position: absolute;
  width: 0;
  height: 0;
  left: 30px;
  right: auto;
  top: auto;
  bottom: -40px;
  border: 20px solid;
  border-color: #5c9fb5 transparent transparent #5c9fb5;
}
</style>
