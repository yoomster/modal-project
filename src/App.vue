<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <input type="text" ref="name" />
  <button @click="handleClick">click me!</button>
  <br />
  <br />

  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up</a>
        <a href="#">login</a>
      </template>
      <h1>Sign up with us</h1>
      <p>We only allow members to continue</p>
    </Modal>
  </teleport>
  <button @click="toggleModal">open modal</button>

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>second one in action!</h1>
    </Modal>
  </div>
  <button @click="toggleModalTwo">open 2nd modal</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue app!!!",
      showModal: false,
      showModalTwo: false,
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
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
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
