<template>
  <div class="index container">
    <div class="card" v-for="smoothie in smoothies" :key="smoothie.id">
      <div class="card-content">
        <i class="material-icons delete" @click="deleteSmoothie(smoothie.id)">delete</i>
        <h2 class="indigo-text">{{ smoothie.title }}</h2>
        <ul class="ingredients">
          <li v-for="(ing, index) in smoothie.ingredients" :key="index">
            <span class="chip">{{ ing }}</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      pageTitle: "This is My Page Title",
      smoothies: [
        {
          id: "1",
          title: "Ninja Brew X",
          slug: "ninja-brew",
          ingredients: ["Milk", "Chocolate", "Mango"]
        },
        {
          id: "2",
          title: "Ninja Juice",
          slug: "ninja-juice",
          ingredients: ["Banana", "Tomato", "Milk"]
        },
        {
          id: "3",
          title: "Ninja Morning",
          slug: "ninja-morning",
          ingredients: ["Grape", "Juice", "Bluberry"]
        }
      ]
    };
  },
  methods: {
    deleteSmoothie(id) {
      this.smoothies = this.smoothies.filter(smoothie => {
        return smoothie.id != id;
      });
    }
  }
};
</script>

<style>
.index {
  margin-top: 30px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 30px;
}
.index h2 {
  font-size: 1.8em;
  margin-top: 0;
  text-align: center;
}
.index .delete {
  position: absolute;
  top: 4px;
  right: 4px;
  cursor: pointer;
  color: #aaa;
  font-size: 1.4em;
}
.ingredients {
  margin: 30px auto;
}
.ingredients li {
  display: inline-block;
}
</style>
