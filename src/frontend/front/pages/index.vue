<template>
  <div>
    <AboutSec />
    <PurposeSec />
    <ContentsSec />
  </div>
</template>

<script>
import AboutSec from '~/components/pages/AboutSec.vue'
import PurposeSec from '~/components/pages/PurposeSec.vue'
import ContentsSec from '~/components/pages/ContentsSec.vue'

export default {
  name: 'TopPage',
  components: { AboutSec, PurposeSec, ContentsSec },
  data() {
    return {
      // breadcrumbs: [
      //   {
      //     name: 'トップページ',
      //     path: '/',
      //   },
      // ],
    }
  },
  computed: {
    breadcrumbs() {
      return [
        {
          name: 'ホーム',
          path: '/',
        },
      ]
    },
  },
}
</script>
