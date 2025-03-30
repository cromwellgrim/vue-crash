<script>
export default {
  data() {
    return { 
      name: 'John Smith',
      status: 'active',
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://vuejs.org'
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive'
      } else {
        this.status = 'active'
      }
    }
  }
};
</script>

<template>
  <h1>Jobs App</h1>
  <h3>{{ name }}</h3>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>
  <p v-text="Hi"></p>
  <h2>Tasks</h2>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
    <a :href="link"> Let anyone choose status</a>
    <br/>
    <button @click="toggleStatus">Change Status</button>
    <br/>
    <button v-on:click="toggleStatus">Change Status</button>
  </ul>
</template>

