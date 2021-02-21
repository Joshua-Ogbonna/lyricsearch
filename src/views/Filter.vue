<template>
    <div class="container">
        <h1>{{heading}}</h1>

        <input type="text" placeholder="Filter List" v-model="input">

        <ul>
            <li v-for="(item, i) in computedList" :key="i" > {{item}} </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                heading: 'Prototype Vue Component',
                frameworks: [
                    'Vue',
                    'React',
                    'Angular',
                    'Backbone',
                    'Ember',
                    'Knockout',
                    'jQuery',
                    // 'Angular'
                ],
                input: ''
            }
        },

        // Computed properties
        computed: {
            computedList() {
                return this.frameworks.filter(item => {
                    return item.toLowerCase().includes(this.input.toLowerCase())
                })
            }
        }
    }
</script>

<style scoped>
    h1 {
        font-family: Arial, Arial, Helvetica, sans-serif;
    }
    ul {
        max-width: 200px;
        margin: 0 auto;
        list-style: none;
        padding: 0;
    }
    ul li {
        background: #42b983;
        color: white;
        padding: 6px;
        border-radius: 6px;
        margin-bottom: 2px;
        max-width: 200px;
    }
    input {
        padding: 10px 6px;
        margin: 20px 10px 10px 10px;
    }
</style>