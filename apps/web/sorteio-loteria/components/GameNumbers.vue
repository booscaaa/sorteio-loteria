<template>
  <div>
    <v-row no-gutters>
      <v-col cols="12" class="d-flex flex-wrap justify-center">
        <v-btn
          class="ma-1"
          fab
          v-for="(number, i) in gameNumbers"
          :key="i"
          :class="isSelectedNumber(number) ? 'btn-active' : ''"
          @click.stop="toggleGameNumber(number)"
          >{{ number }}</v-btn
        >
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="d-flex flex-wrap justify-center">
        {{ selectedNumbers }}
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class Numbers extends Vue {
  selectedNumbers: Array<number> = [];

  isSelectedNumber(num: number) {
    return this.selectedNumbers.some((e) => e === num);
  }

  toggleGameNumber(num: number) {
    if (this.selectedNumbers.some((e) => e === num)) {
      this.removeNumberFromSelected(num);
    } else {
      if (this.selectedNumbers.length <= 5) {
        this.selectedNumbers.push(num);
      }
    }
  }
  removeNumberFromSelected(num: number) {
    if (this.selectedNumbers.some((e) => e === num)) {
      let index = this.selectedNumbers.map((b) => b).indexOf(num);
      if (index > -1) {
        this.selectedNumbers.splice(index, 1);
      }
    }
  }

  get gameNumbers(): Array<number> {
    let initNumbers: Array<number> = [];
    for (let num: number = 1; num <= 60; num++) {
      initNumbers.push(num);
    }
    return initNumbers;
  }
}
</script>

<style lang="scss" scoped>
.btn-active {
  background-color: #21986A !important;
}
</style>
