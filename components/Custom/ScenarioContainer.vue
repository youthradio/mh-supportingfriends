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
        v-for="(option, id) in scenario.options"
        :key="`${option}-${id}`"
        :class="['basis-50','position-relative', 'btm-left-in', 'pointer', 'round', 'talk-bubble', (id === 0 ? 'meanResponse' : 'niceResponse'), (selectedOption > -1 ? (id === 0 ? 'sadSun':'happySun'):'')]"
        @click="processOption(id)"
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
@import "~@/css/mixins";

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
}

.scenario-container{
  background-color: #EFEFEF; //temporary
  border: 8px solid #5C9FB5;
  border-radius: 50px;
  .textContent{
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
  text-align: center;
  margin: 0 2rem 0 2rem;
  }
  margin: 1rem 0 1rem 0;
}
/*.scenario-container:before,
.scenario-container:after {
  //makes a after _and_ before ruleset dedicated to what would be a single psudo-element
  content: ' ';
  position: absolute;
  left: 20px;
  bottom: -30px;
  width: 40px;
  height: 40px;
  background-color: #fff;
  border: 5px solid #333;
  -webkit-border-radius: 28px;
  -moz-border-radius: 28px;
  border-radius: 28px;
}*/

/*.scenario-container:after {
  width: 20px;
  height: 20px;
  left: 5px;
  bottom: -40px;
  -webkit-border-radius: 18px;
  -moz-border-radius: 18px;
  border-radius: 18px;
}*/

.niceResponse{
  .textContent{
  padding: 6px;
  }
}

.meanResponse{
  .textContent{
  padding: 6px;
  }
}

.meanResponse:hover{
  background-color: none;
  //outline: 6px solid $grey;
}

.niceResponse:hover{
  background-color: none;
  //outline:6px solid $grey;
}

.happySun:after{
content: '';
background: url('~assets/images/sun-wake.png') no-repeat;
position: absolute;
overflow: hidden;
width: 80px;
height: 80px;
top: 11.5rem;
right: -1.5rem;
  @include breakpoint(medium){
    top: 8.5rem;
    right: -1rem;
  }
}
.sadSun:after{
content: '';
background: url('~assets/images/sad-wake.png') no-repeat;
position: absolute;
overflow: hidden;
width: 120px;
height: 120px;
top: -60.5px;
right: 0rem;
left: -3.5rem;
@include breakpoint(medium){
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
.meanResponse, .niceResponse{
  .textContent{
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;
    text-align: center;
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
.niceResponse, .meanResponse{
  .textContent{
  background-color: #5C9FB5;
  color: #EFEFEF;
  }
  .textContent:hover{
  background-color: #5C9FB5;
  }
}

.textContent {
  padding: 6px;
  @media screen and (min-width: 450px) {
    min-height: 250px;
  }
}

.talk-bubble {
  display: inline-block;
  position: relative;
  height: auto;
  background-color: #5C9FB5;

  margin: 30px;
  padding: 30px;
  border-radius: 30px;
  border-color: grey;
}
.round{
  border-radius: 30px;
}

/*Right triangle, placed bottom left side slightly in*/
.btm-left-in:before {
  content: ' ';
  position: absolute;
  width: 0;
  height: 0;
  left: 30px;
  right: auto;
  top: auto;
  bottom: -40px;
  border: 20px solid;
  border-color: #5C9FB5 transparent transparent #5C9FB5;
}
</style>
