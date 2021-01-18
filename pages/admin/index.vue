<template>


  <div class="container">

    <div class="row">

      <h1 class="title text-center">
        АДМИНКА
      </h1>
    </div>
    <div class="row">
      <h2 class="title text-center">
        <nuxt-link to="admin/articles">К списку статей</nuxt-link>      </h2>
    </div>
    <div class="row">


      <h2 class="title text-center">
<nuxt-link to="admin/categories">К списку категорий</nuxt-link>      </h2>
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
