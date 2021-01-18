<template>


    <div class="container">

      <div class="row">

        <h1 class="title text-center">
         ГЛАВНАЯ
        </h1>


      </div>
      <div class="row" v-for="t in test">

        <div class="col"><b>{{
           t.email
          }}</b><br></div>

        <div class="col">{{ t.password }}<br></div>
        <div class="col">{{ t.role }}<br></div>
        <div class="col">{{ t.id }}<br></div>

      </div>
      <div class="row">
        <input type="text">
        <input type="number">
        <input type="password">
      </div>

      <div class="row">
        <textarea></textarea>
      </div>

      <div class="row">
        <label>I agree to the terms
          <input type="checkbox"/>
          <span class="checkbox"></span>
        </label>
      </div>

      <div class="row">
        <label>Apples
          <input type="radio" name="fruit" checked/>
          <span class="radiobutton"></span>
        </label>
        <label>Oranges
          <input type="radio" name="fruit"/>
          <span class="radiobutton"></span>
        </label>
      </div>

      <div class="row">
        <div class="col">
          <button>Click Me</button>
        </div>
        <div class="col">
          <button class="danger">Click Me</button>
        </div>
        <div class="col">
          <button class="success">Click Me</button>
        </div>
      </div>
      <div class="row">
        <table>
          <tr>
            <th>Company</th>
            <th>Q1</th>
            <th>Q2</th>
            <th>Q3</th>
            <th>Q4</th>
          </tr>
          <tr>
            <td>Microsoft</td>
            <td>20.3</td>
            <td>30.5</td>
            <td>23.5</td>
            <td>40.3</td>
          </tr>
          <tr>
            <td>Google</td>
            <td>50.2</td>
            <td>40.63</td>
            <td>45.23</td>
            <td>39.3</td>
          </tr>
          <tr>
            <td>Apple</td>
            <td>25.4</td>
            <td>30.2</td>
            <td>33.3</td>
            <td>36.7</td>
          </tr>
          <tr>
            <td>IBM</td>
            <td>20.4</td>
            <td>15.6</td>
            <td>22.3</td>
            <td>29.3</td>
          </tr>
        </table>
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
