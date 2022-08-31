<template>
  <v-card>
    <v-app-bar
      absolute
      prominent
      color="#0E2997"
      :src="image_src"
      dark
      fixed
      scroll-off-screen
    >
      <template #img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(14,41,151,.5), rgba(14,41,151,.5)"
        ></v-img>
      </template>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title
        class="text-h2 font-weight-bold white--text mb-1"
        style="cursor: pointer"
        @click="returnTop"
      >
        {{ Title }}
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
      <template #extension>
        <v-tabs align-with-title>
          <v-tab @click="returnTop">Hardness</v-tab>
          <v-tab>Tab 2</v-tab>
          <v-tab>Tab 3</v-tab>
        </v-tabs>
      </template>
    </v-app-bar>
  </v-card>
</template>

<script scoped>
export default {
  name: 'TheHeader',
  data: () => ({
    Title: 'Hydledge',
    image_src: require('@/assets/img/falling.jpeg'),
  }),
  methods: {
    returnTop() {
      this.$router.push('/')
    },
  },
}
</script>