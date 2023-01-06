<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="8" lg="6" xl="6">
      <GameNumbers />
    </v-col>
  </v-row>
</template>

<script>
import GameNumbers from '~/components/GameNumbers.vue';
export default {
  components: {
    GameNumbers
  }
}
</script>
