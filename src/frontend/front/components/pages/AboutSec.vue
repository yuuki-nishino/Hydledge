<template>
  <section class="about-img">
    <section class="about-rgb">
      <v-container>
        <v-row
          class="d-flex justify-center align-center text-center"
          align-content="center"
          style="height: 50vh"
        >
          <v-col cols="12" class="white--text">
            <div class="text-h2 font-weight-black mb-10">Hydledgeとは？</div>
            <div class="text-h4 mt-10">Hydro (水) ＋ Knowledge(知識)</div>
            <div class="text-h4">水に関する情報をデータを基に発信</div>
          </v-col>
        </v-row>
      </v-container>
    </section>
  </section>
</template>



<script scoped>
export default {
  name: 'AboutSec',
  data: () => ({}),
  methods: {},
}
</script>

<style scoped>
.about-img {
  background-image: url('~@/assets/img/water2.jpeg');
  background-position: center;
  width: 100%;
  height: 50vh;
}

.about-rgb {
  background: rgba(14 41 151 / 40%);
  width: 100%;
  height: 50vh;
}
</style>