<template>
  <div class="Container">
    <div class="bigImageContainer">
      <div class="topLayer">
        <div class="bigImage">
          <img :src="scenario.mainImg">
        </div>
        <div class="textContent">
          {{ scenario.text }}
        </div>
      </div>
    </div>
    <div class="flex-container">
      <div v-for="option in scenario.options" :key="option" class="bigImageContainer">
        <div class="topLayer">
          <div class="bigImage">
            <img :src="scenario.Img1">
          </div>
          <div class="textContent">
            <!-- option IN option 😒-->
            {{ option.option }}
          </div>
        </div>
      </div>
    </div>

    <div class="flex-container">
      <div class="optionContainer">
        <h5>Results:</h5>
        <div class="textContent">
          {{ scenario.options[0].result }}
        </div>
      </div>
      <div class="optionContainer">
        <h5>Results:</h5>
        <div class="textContent">
          {{ scenario.options[1].result }}
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
      clickedElement: false
    }
  },
  methods: {
    findClicked: () => {

    }
  }
}
</script>
  <style scoped lang="scss">
  @import "~@/css/vars";
  @import "~@/css/base";
    .flex-container{
        display: flex;
        padding-top: 10px;
        justify-content: center;
        /* bigImageContainer is reused outside of flex so this wouldn't apply to anything outside of a flexbox anyway */
        .bigImageContainer{
            flex-basis: 50%;
        }
        .optionContainer{
          flex-basis: 50%;
          h5{
            padding: 10px;
          }
        }
    }

    .optionContainer{
      color: grey;
    }

    .correct-result{
      color: $green;
    }

    .bigImageContainer{
    position: relative;
    /* make container retain a size based on the text content*/
    max-width: 100%;
    max-height: 100%;
    overflow: hidden;
    margin: 0 10px 0 10px;

    }
    .bigImage img{
    z-index: -1;
    position: absolute;
    /* make image size based on the parent container, which is dependent on text */
    height: 100%;
    width: 100%;
    /* clean stretching */
    object-fit: cover;
    object-position: center;
    }
    .textContent{
    z-index: 1;
    padding: 10px;
    margin: 0 auto;
    height: 300px;
    }
    </style>
