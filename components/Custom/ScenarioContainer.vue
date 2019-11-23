<template>
  <div class="Container">
    <BigImageContainer />
    <div class="flex-container">
      <BigImageContainer class="big-image-comtainer" />
      <BigImageContainer class="big-image-comtainer" />
    </div>
  </div>
</template>

<script>
import BigImageContainer from '~/components/custom/BigImageContainer'

export default {
  components: {
    BigImageContainer
  }

}
</script>
  <style scoped lang="scss">
    .flex-container{
        display: flex;
        padding-top: 10px;
        /* flex doesn't have gaps so we're doing margin hacks lol */
        margin:0 0 0 -10px;
        justify-content: center;
        .big-image-comtainer{
            padding-right: 10px;
            padding-left: 10px;
        }
    }
    </style>
