<template>
  <div class="container">
    <HeaderContainer />
    <article>
      <p>
        {{ articleData.opening }}
      </p>
      <div
        v-for="scenario in articleData.scenarios"
        :key="scenario.title"
      >
        {{ scenario }}
      </div>

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
import ArticleData from '../data/data.json'
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
  asyncData (ctx) {
    return {
      articleData: ArticleData.content
    }
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
