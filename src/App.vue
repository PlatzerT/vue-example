<template>
  <div id="app">
    <h3>Example</h3>
    <form @submit.prevent="handleSubmit">
      <span>Enter new subject:</span>
      <input type="text" v-model="newSubject" />
      <button>Add subject</button>
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
  color: white;
  background: #2c3e50;
  outline-width: none;
  border: none;
  padding: 6px 12px;
  border-radius: 5px;
  font-weight: 500;
}

button:hover {
  background: #1e2b38;
}

button:focus {
  background: #34495e;
}

.light {
  color: #313131;
  background: #e2e2e2;
}
</style>
