<template>


  <div class="container">


    <div class="row">
      <h2 class="title text-center">
        Список категорий
      </h2>
    </div>

    <div class="row">
      <div class="row">
        <table>
          <tr>
            <th>ID</th>
            <th>del</th>

            <th>Title</th>
            <th>Description</th>
            <th>ParentId</th>

          </tr>
          <tr v-for="category in categories">
            <td>{{ category.id }}</td>
            <td>
              <button class="danger" @click="del(category.id)">X</button>
            </td>
            <td>
              <nuxt-link :to="'/admin/categories/' + category.id"> {{ category.title }}</nuxt-link>
            </td>
            <td>{{ category.description }}</td>
            <td>{{ category.parentId }}</td>

          </tr>

        </table>
      </div>
    </div>
    <hr>
    <h2>
      Добавить категорию
    </h2>
    <div class="row">
      <input type="text" placeholder="Заголовок" v-model="title">
      <select v-model="parentCategory">
        <option v-for="category in categories" :value="category.id">{{ category.title }}</option>
      </select>
    </div>

    <div class="row">
      <textarea placeholder="Описание" v-model="description"></textarea>
    </div>
    <div class="row">

      <div class="col">
        <button class="success" @click="send">Отправить</button>
      </div>
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
      categories: [],
      title: '',
      description: '',
      parentCategory: null,

    }
  },
  methods: {
    async fetchNet() {
      this.categories = await this.$axios.$get('http://localhost:58022/api/categories')
    },
    async send() {
      console.log({
        title: this.title,
        description: this.description,
        parentCategory: this.parentCategory
      })
      await this.$axios.$post('http://localhost:58022/api/categories', {
        title: this.title,
        description: this.description,
        parentId: this.parentCategory ?? null
      })
      this.title = ''
      this.description = ''
      this.parentCategory = ''
      await this.fetchNet()
    },
    async del(id) {
      console.log(id)
      await this.$axios.$delete('http://localhost:58022/api/categories/' + id)
      await this.fetchNet()
    }
  },
  async mounted() {
    await this.fetchNet()
  }
}
</script>

<style>

</style>
