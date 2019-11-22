<template>
  <div class="container">
    <HeaderContainer />
    <article>
      <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Mus mauris vitae ultricies leo integer. Odio ut sem nulla pharetra. Mauris augue neque gravida in fermentum et. Placerat duis ultricies lacus sed. Proin fermentum leo vel orci porta non pulvinar neque laoreet. Maecenas ultricies mi eget mauris. Malesuada fames ac turpis egestas integer eget aliquet nibh. Urna et pharetra pharetra massa massa ultricies. Interdum velit laoreet id donec.</p>
      <p>Vitae purus faucibus ornare suspendisse sed nisi. Dignissim cras tincidunt lobortis feugiat vivamus at. Lorem mollis aliquam ut porttitor. Mauris in aliquam sem fringilla ut morbi tincidunt augue. Lorem ipsum dolor sit amet. Nibh mauris cursus mattis molestie a iaculis at. Vulputate sapien nec sagittis aliquam malesuada bibendum. Viverra suspendisse potenti nullam ac tortor vitae purus faucibus. Interdum consectetur libero id faucibus nisl tincidunt eget. Vulputate enim nulla aliquet porttitor lacus luctus. Ornare arcu dui vivamus arcu felis bibendum ut tristique. Dignissim cras tincidunt lobortis feugiat vivamus at. Turpis massa tincidunt dui ut ornare lectus.</p>

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
    </article>
    <ShareContainer />
    <RelatedPostsContainer />
    <FooterContainer />
  </div>
</template>

<script>

import CommonUtils from '../mixins/CommonUtils'
import RelatedPostsContainer from '~/components/RelatedPosts/RelatedPostsContainer'
import HeaderContainer from '~/components/Header/HeaderContainer'
import ShareContainer from '~/components/custom/ShareContainer'
import FooterContainer from '~/components/Footer/FooterContainer'

export default {
  components: {
    RelatedPostsContainer,
    HeaderContainer,
    ShareContainer,
    FooterContainer
  },
  mixins: [
    CommonUtils
  ],
  data () {
    return {
    }
  },
  computed: {},
  watch: {

  },
  async asyncData (ctx) {

  },
  mounted () {
  },
  methods: {

  }
}
</script>

<style lang="scss" scoped>
@import "~@/css/vars";
@import "~@/css/base";

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
