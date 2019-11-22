<template>
  <div class="bigImageContainer">
    <div class="topLayer">
      <div class="bigImage">
        <img src="https://picsum.photos/600/300">
      </div>
      <div class="textContent">
        Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
        <br> <br>
        Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet.
      </div>
    </div>
  </div>
</template>
  <style scoped lang="scss">
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
    width: 300px;
    height: 300px;
    }
    </style>
