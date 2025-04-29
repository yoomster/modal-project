<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <input type="text" ref="name" />
  <button @click="handleClick">click me!</button>
  <br />
  <br />

  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up</a>
        <a href="#">login</a>
      </template>
      <h1>Sign up with us</h1>
      <p>We only allow members to continue</p>
    </Modal>
  </div>
  <button @click="toggleModal">open modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue app!!!",
      header: "Sign up first",
      text: "We only allow members",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
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
  color: #42b983;
  padding-bottom: 10px;
  border-bottom: 2px solid #42b983;
  display: inline-block;
}
</style>
