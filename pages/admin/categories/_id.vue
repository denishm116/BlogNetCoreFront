<template>


  <div class="container">


    <div class="row">
      <h2 class="title text-center">
        Одна категория
      </h2>
    </div>


    <div class="row">
      <h3 class="title text-center">
        {{category.title}}
      </h3>
    </div>
{{category.description}}<br>
{{category.parent}}<br>



  </div>


</template>

<script>
import Navbar from "@/components/frontend/navigation/Navbar";

export default {
  components: {Navbar},

  data() {
    return {
      category: {}
    }
  },
  methods: {
    async fetchNet() {
      this.category = await this.$axios.$get('https://localhost:44329/api/categories/' + this.$route.params.id)
    }
  },
  async mounted() {
    await this.fetchNet()
  }
}
</script>

<style>

</style>
