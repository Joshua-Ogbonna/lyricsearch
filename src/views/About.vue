<template>
  <div class="container">
    <h1>Shop Watcher</h1>
    <div>
      Black Friday sale
      <p><strike>Was {{oldDiscount}} % </strike> <br></p>
      <p><strong> Now {{discount}}% off </strong> <br></p>
      <a href="#" @click="updateDiscount">updateDiscount</a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      oldDiscount: 0,
      discount: 5
    }
  },

  watch: {
    discount(newValue, oldValue) {
      this.oldDiscount = oldValue
    }
  },

  methods: {
    updateDiscount() {
      this.discount += 5
    }
  },
};
</script>

<style scoped>
.container {
  margin: 0 auto;
  max-width: 600px;
  padding: 30px;
  margin: 0;
  font-family: "Avenir", Helvetica, sans-serif;
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
