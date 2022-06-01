<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="modalShow">
    <Modal @toggleModal="modalShow = false" header="Modal title" content="Modal content">
      <h1> Hello world from app.vue</h1>
      <template v-slot:action>
        <a href="#">Link 1</a>
        <a href="#">Link 2</a>
        <a href="#">Link 3</a>
      </template>  
    </Modal>
  </div>
  <button @click="modalShow = true">Click me</button>
</template>

<script>
import Modal from "./components/Modal.vue"

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: "My first vue app!",
      modalShow: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      // add class to the ref.name active, e.g class="active"
      this.$refs.name.classList.add("active")
      // focus to the refs
      this.$refs.name.focus()
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
