<template>
  <div>
    <!-- <AboutSec /> -->
    <PurposeSec />
    <MissionSec />
    <ContentsSec />
  </div>
</template>

<script>
// import AboutSec from '~/components/pages/AboutSec.vue'
import PurposeSec from '~/components/pages/PurposeSec.vue'
import MissionSec from '~/components/pages/MissionSec.vue'
import ContentsSec from '~/components/pages/ContentsSec.vue'

export default {
  name: 'TopPage',
  components: { PurposeSec, MissionSec, ContentsSec },
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
