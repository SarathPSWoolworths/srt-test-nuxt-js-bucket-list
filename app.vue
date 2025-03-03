<template>
  <div>
    <h1>Bucket List</h1>
    <input v-model="newItem" @keyup.enter="addItem" placeholder="Add a new item" />
    <button @click="addItem">Add</button>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item }}
        <button @click="removeItem(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>
<script setup>
useHead({
  title: 'Srt Testing Nuxt',
  meta: [
    {
      name: 'description',
      content: 'This is a test page for SRT'
    }
  ]
}); 
</script>

<script>
export default {
  data() {
    return {
      items: []
    };
  },
  methods: {
    addItem() {
      if (this.newItem.trim() !== '') {
        this.items.push(this.newItem);
        this.newItem = '';
      }
    },
    removeItem(index) {
      this.items.splice(index, 1);
    }
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
}

input {
  margin-right: 10px;
}

button {
  margin-left: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 5px 0;
}
</style>
