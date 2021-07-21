<template>
  <div class="hello">
    <h1 ref="title">{{ msg }}</h1>
    <p v-if="name">{{ name }}</p>
    <p>{{ fullName }}</p>
    <h2>Lista</h2>
    <ul>
      <li :key="index" v-for="(n, index) in names">
        {{n.name}}
      </li>
    </ul>
    <button @click="atualizarNome()">Atualizar</button>
    <input type="text" v-model="name">
    <p>{{name}}</p>
  </div>
</template>

<script>
export default {
  beforeCreate() {
    console.log(this.name)
  },
  created() {
    console.log(this.name)
  },
  mounted() {
    console.log(this.$refs.title.textContent)
  },
  beforeUpdate() {
    console.log('beforeUpdate', this.name)
  },
  updated() {
    console.log('update', this.name)
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: () => {  
    return {
      name: null,
      lastName: 'Silva',
      names: [
        { id: 1, name: "João" },
        { id: 2, name: 'Maria'},
      ]
    }
  },
  computed: {
    fullName() {
      return `${this.name} ${this.lastName}`
    }
  },
  watch: {
    name(newValue) {
      console.log(newValue)
    }
  },
  methods: {
    atualizarNome() {
      this.name = 'Nome atualizado'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
