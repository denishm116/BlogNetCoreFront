<template>


  <div class="container">


    <div class="row">
      <h2 class="title text-center">
        Список Статей
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
            <th>Categories</th>

          </tr>
          <tr v-for="article in articles">
            <td>{{ article.id }}</td>
            <td>
              <button class="danger" @click="del(article.id)">X</button>
            </td>
            <td>
              <nuxt-link :to="'/admin/article/' + article.id"> {{ article.title }}</nuxt-link>
            </td>
            <td>{{ article.description }}</td>
            <td>
              <div v-for="category in article.categories">
                {{ category.title }}
              </div>

            </td>

          </tr>

        </table>
      </div>
    </div>
    <hr>
    <h2>
      Добавить статью
    </h2>
    <div class="row">
      <input type="text" placeholder="Заголовок" v-model="title">
      <select v-model="selectedCategories" multiple size="3">
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
      articles: [],
      article: {
        title: '',
        description: '',
        categories: []
      },
      title: '',
      description: '',
      parentCategory: null,
      categories: [],
      selectedCategories: []

    }
  },
  computed: {
    cats() {
      let c = [];
      this.categories.forEach((cat) => {
        this.selectedCategories.forEach(item => {
          if (item === cat.id)
            c.push(cat)

        })
      })
      return c
    }
  },
  methods: {
    async fetchArticles() {
      this.articles = await this.$axios.$get('http://localhost:58022/api/articles')
    },
    async fetchCategories() {
      this.categories = await this.$axios.$get('http://localhost:58022/api/categories')
    },

    async send() {
      this.article =
        {
          Article: {
            title: this.title,
            description: this.description,
          }
       ,
          Categories: [this.cats]
        }



      console.log(JSON.stringify(this.article))
      await this.$axios.$post('http://localhost:58022/api/articles', this.article)
      this.title = ''
      this.description = ''
      this.categories = ''
      this.cats = []
      await this.fetchArticles()
    },
    async del(id) {
      await this.$axios.$delete('http://localhost:58022/api/articles/' + id)
      await this.fetchArticles()
    }
  },
  async mounted() {
    await this.fetchArticles()
    await this.fetchCategories()
  }
}
</script>

<style>

</style>
