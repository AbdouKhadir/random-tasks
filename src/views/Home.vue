<template>
  <div class="home">
    <b-container>
      <b-row align-h="between">
        <b-col lg="4" class="mb-5"><name-shuffler/></b-col>
        <b-col lg="6" ><random-number/></b-col>
        
      </b-row>
      
    </b-container>
    
  </div>
</template>

<script>
// @ is an alias to /src

import NameShuffler from '@/components/NameShuffler'
import RandomNumberVue from "@/components/RandomNumber";

export default {
  name: "Home",
  components: {
    "name-shuffler": NameShuffler,
    "random-number": RandomNumberVue
  }
};
</script>
