<template>
  <div class="container">
    <HeaderContainer />
    <article>
      <p>
        {{ articleData.opening }}
      </p>
    </article>
    <div
      v-for="scenario in articleData.scenarios"
      :key="scenario.title"
    >
      {{ scenario }}
    </div>
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

</style>
