<template>


  <div class="container">


    <div class="row">
      <h2 class="title text-center">
        Одна статья
      </h2>
    </div>


    <div class="row" v-for="t in test">
      <div class="col"><b>{{
          new Date(t.date).getDate() + '.' + (+(new Date(t.date).getMonth()) + 1) + '.' + new Date(t.date).getFullYear()
        }}</b><br></div>
      <div class="col">{{ t.temperatureC }}<br></div>
      <div class="col">{{ t.temperatureF }}<br></div>
      <div class="col">{{ t.summary }}<br></div>

    </div>


  </div>


</template>

<script>
import Navbar from "@/components/frontend/navigation/Navbar";

export default {
  components: {Navbar},
  comments: {
    Navbar
  },
  data() {
    return {
      test: 'Test'
    }
  },

}
</script>

<style>

</style>
