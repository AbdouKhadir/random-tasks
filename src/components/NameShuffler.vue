<template>
  <b-card border-variant="info" header="Names Randomizer" align="center">
      <b-list-group>
        <b-list-group-item
          class="d-flex justify-content-between align-items-center"
          v-for="(name, idx) in listNames" :key="idx"
        >
          {{(idx + 1) + ". " + name}}
          <b-icon icon="x-circle" scale="2" variant="danger" @click="deleteName(idx)"></b-icon>
        </b-list-group-item>
        <b-list-group-item 
          v-if="!listNames.length"
          style="border-style: dashed; background-color: red"
        >
          <i>Add Names to Get started</i>
          
        </b-list-group-item>
      </b-list-group>

      <b-form class="mt-5" @submit.prevent="addNewPerson()">
        <b-form-input type="text"  v-model="newPersonName" placeholder="Enter a new name"></b-form-input>
        <b-row class="d-flex justify-content-around align-items-center mt-3">
          <b-button type="submit" variant="primary">
            <b-icon icon="plus" aria-hidden="true"></b-icon>
            Add Name
          </b-button>
          <b-button  @click="shuffleList()" variant="danger" :disabled="listNames.length<2">
            Shuffle List
            <b-icon class="ml-2" icon="shuffle" aria-hidden="true"></b-icon>
          </b-button>
        </b-row>
        
      </b-form>
  </b-card>
      
</template>

<script>
export default {
  data() {
    return {
      listNames: ["David", "Leo", "Mouhammad", "Saliou"],
      newPersonName: ""
    }
  },
  methods: {
    generateId(){
      const characters = "abcdefghijklmnopqrstuvwxyz1234567890".split("");
      var id = "";
      for (let index = 0; index < 6; index++) {
        var ranIndx = Math.floor(Math.random()*(characters.length));
        id += characters[ranIndx];
      }
      return id;
    },

    deleteName(id) {
      this.listNames.splice(id,1);
    },

    addNewPerson() {
      console.log("asking to add: " + this.newPersonName )
      if (this.newPersonName) {
        this.listNames.push(this.newPersonName);
        this.newPersonName = "";
      }
    },
    shuffleList() {
      this.listNames = this.listNames.sort(() => Math.random() - 0.5);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
