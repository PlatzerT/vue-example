<template>
  <div id="app">
    <h3>Example</h3>
    <form @submit.prevent="handleSubmit">
      <span>Enter new subject:</span>
      <input type="text" v-model="newSubject" />
      <button class="solid">Add subject</button>
    </form>
    <ul>
      <li v-for="(s, index) in subjects" v-bind:key="index">
        <span>{{ s }}</span>
        <button class="light" @click="deleteSubject(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      newSubject: "",
      subjects: [],
    };
  },
  methods: {
    handleSubmit() {
      this.subjects.push(this.newSubject);
      this.newSubject = "";
    },
    deleteSubject(index) {
      this.subjects = this.subjects.filter((s, i) => i !== index);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

form {
  display: flex;
  column-gap: 10px;
  align-items: center;
}

button {
  outline-width: none;
  border: none;
  padding: 6px 12px;
  border-radius: 5px;
  font-weight: 500;
  border: 1px solid transparent;
  transition-property: all;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
  cursor: pointer;
}

.solid {
  color: white;
  background: #2c3e50;
}

.solid:hover {
  background: #1e2b38;
}

.solid:focus {
  background: #34495e;
}

.light {
  color: #1f2937;
  background: white;
  border: 1px solid #e5e7eb;
}

.light:hover {
  background-color: #f9fafb;
  box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
}

.light:focus {
  background: #d1d5db;
  box-shadow: none;
}
</style>
