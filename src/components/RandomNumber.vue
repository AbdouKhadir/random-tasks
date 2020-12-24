<template>
  <b-card border-variant="success" header="Generate Number Between Min and Max" align="center">
    <b-row>
      <b-col style="font-size:100px"> {{luckyNumber}}</b-col>
    </b-row>
    <template #footer>
      <b-row class="d-flex justify-content-around align-items-end">
        <b-col md="3" class="d-flex flex-column align-items-start">
          <label for="borderleft-input">Minimum</label>
          <b-form-input id="borderleft-input" type="number" @blur="resetInput"  v-model="borderLeft" min="0"></b-form-input>
        </b-col>
        <b-col md="3" class="d-flex flex-column align-items-start">
          <label for="borderright-input">Maximum</label>
          <b-form-input id="borderright-input" type="number" @blur="resetInput"  v-model="borderRight"  min="0"></b-form-input>
        </b-col>
        <b-col class="mt-4">
          <b-button  @click="generateLuckyNumber()" variant="success">
            Lucky Number
            <b-icon class="ml-2" icon="dice5" aria-hidden="true"></b-icon>
          </b-button>
        </b-col>
      </b-row>
    </template>
  </b-card>   
</template>

<script>
export default {
  data() {
    return {
      borderLeft: 0,
      borderRight: 0,
      luckyNumber: 0
    }
  },
  methods: {
    generateLuckyNumber() {
      this.resetInput();
      var diff = Math.abs(this.borderLeft - this.borderRight)
      this.luckyNumber = Math.floor(this.borderLeft + Math.random()*diff);
    },

    resetInput() {
      this.borderRight = parseInt(this.borderRight || 0);
      this.borderLeft = parseInt(this.borderLeft || 0);
      if (this.borderLeft > this.borderRight) {
        var tempo = this.borderRight;
        this.borderRight = this.borderLeft;
        this.borderLeft = tempo;
      }
      if (!(this.luckyNumber <= this.borderRight && this.luckyNumber >= this.borderLeft)) {
        this.luckyNumber = this.borderLeft;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
