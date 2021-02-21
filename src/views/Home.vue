<template>
  <div class="container">
    <!-- <input type="number" v-model="incrementOne">
    <h3>Get Input:  {{incrementOne}} </h3>
    <h5>Divide By Two: {{divideByTwo}} </h5> -->
    <h1>Deep Watcher</h1>
    <div>
      <h4> {{product.label}} </h4>
      <h5> {{product.price}} (${{discount}}% Off)  </h5>
      <a href="#" @click="updatePrice">Reduce Price!</a>

      <br><br>

      <br><br>
      <button @click="getNewName">Click to generate user</button>
      <p> {{author}} </p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      // count: -1,
      // divideByTwo: 0
      discount: 0,
      product: {
        price: 25,
        label: 'Blue Juice'
      },
      author:'',
      data: {}
    }
  },

  computed: {
    // incrementOne: {
    //   get() {
    //     return this.count + 1
    //   },
    //   set(val) {
    //     this.count = val - 1,
    //     this.divideByTwo = val / 2
    //   }
    // }
    authorName() {
      return this.authors ? this.authors[0].bio.name : 'No name'
    }
  },
  methods: {
    updatePrice() {
      if (this.product.price < 1) return
      this.product.price--
    },
    async getNewName() {
      await fetch('https://randomuser.me/api/').then(response => response.json()).then(data => {
        this.data = data.results[0].name
        // console.log(data.results)
      })
    }
  },

  watch: {
    'product.price'() {
      this.discount++
    },
    data(newValue, oldValue) {
      this.author = newValue.first
      alert(`Name changed from ${oldValue.first} to ${newValue.first} `)
    }
  }
}
</script>
<style scoped>
.container {
  margin: 0 auto;
  padding: 30px;
  max-width: 600px;
  font-family: 'Avenir', Helvetica, sans-serif;
  margin: 0;

}

a {
  display: inline-block;
  background: rgb(235, 50, 50);
  border-radius: 10px;
  font-size: 14px;
  color: white;
  padding: 10px 20px;
  text-decoration: none;

}
</style>