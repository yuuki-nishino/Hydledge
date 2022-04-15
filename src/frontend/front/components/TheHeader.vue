<template>
  <v-app-bar color="primary lighten-1" dense height="64" fixed>
    <v-toolba-title class="text-h3 font-weight-bold white--text">
      {{ Title }}
    </v-toolba-title>
  </v-app-bar>
</template>

<script scoped>
export default {
  name: 'TheHeader',
  data: () => ({
    Title: 'WaterBase',
  }),
}
</script>