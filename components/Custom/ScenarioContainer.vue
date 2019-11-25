<template>
  <div class="Container">
    <div class="bigImageContainer">
      <div class="topLayer">
        <div class="bigImage">
          <img :src="scenario.mainImg">
        </div>
        <div class="textContent">{{ scenario.text }}</div>
      </div>
    </div>
    <div class="flex-container">
      <div class="bigImageContainer">
    <div class="topLayer">
      <div class="bigImage">
        <img :src="scenario.Img1">
      </div>
      <div class="textContent">
        Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
        <br> <br>
        Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
      </div>
    </div>
  </div>
    <div class="bigImageContainer">
      <div class="topLayer">
          <div class="bigImage">
            <img :src="scenario.Img2">
          </div>
          <div class="textContent">
            Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
            <br> <br>
            Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
          </div>
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
  }
}
</script>
  <style scoped lang="scss">
    .flex-container{
        display: flex;
        padding-top: 10px;
        justify-content: center;
        .big-image-comtainer{
            padding-right: 10px;
            padding-left: 10px;
        }
    }

    .bigImageContainer{
    position: relative;
    /* make container retain a size based on the text content*/
    max-width: 100%;
    max-height: 100%;
    overflow: hidden;
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
    .testClass{
        background-color: blue;
    }
    </style>
