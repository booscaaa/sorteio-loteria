<template>
  <div>
    <v-row>
      <v-col cols="12" class="d-flex flex-wrap justify-center">
        <h1>Como Jogar</h1>
        <p style="text-align: center">
          A Mega-Sena dos Guri paga milhões para o acertador dos 6 números
          sorteados (brincadeira kkk). O jogo consiste em 60 números disponíveis
          no volante de a​postas. O jogador deve marcar 6 números no volante e
          clicar em sortear. O Jogo irá lhe informar o resutado do sorteio e a
          porcentagem de acertos da sua aposta. Boa Sorte!!!
        </p>
      </v-col>
    </v-row>
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
        <span>Numeros Selecionados:</span>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="d-flex flex-wrap justify-center">
        <v-btn
          :ripple="false"
          depressed
          class="ma-1"
          fab
          v-for="(number, i) in 6"
          color="#21986a"
          :key="i"
          style="cursor: default"
          >{{ mySelectedNumbers[i] }}</v-btn
        >
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" class="d-flex flex-wrap justify-center">
        <v-btn
          width="360"
          :disabled="mySelectedNumbers.length <= 5"
          color="#FF9F0E"
          class="ma-1"
          >Sortear</v-btn
        >
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
  get mySelectedNumbers(): Array<number> {
    return this.selectedNumbers.sort((a, b) => a - b);
  }
}
</script>

<style lang="scss" scoped>
.btn-active {
  border: 3px solid #21986a !important;
}
</style>
