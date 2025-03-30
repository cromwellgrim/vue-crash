<script>
export default {
  data() {
    return { 
      status: 'active',
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://vuejs.org',
      users: [],
      user: {
        name: '',
        email: '',
        status: 'inactive'
      }
    };
  },
  computed: {
    ifFormInvalid() {
      return this.name === '' || this.email === '';
    }
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
    },
    addUser() {
      this.users.push({
        name: this.user.name,
        email: this.user.email
      });

      this.user.name = '';
      this.user.email = '';

      console.log(this.users);
    }
  },
  componenets: { UserList }
};
</script>

<!-- a simple colon : is the same as saying v-bind: -->
<!-- using @ symbol is the same as saying v-on: -->

<template>

  <h1>Jobs App</h1>

  <form @submit.prevent="addUser">
    <div>
      <h3>Name</h3>
      <input
        type="text"
        placeholder="enter your name"
        @input="e => user.name = e.target.value"
      />
      <h3>Your Name:&nbsp;{{ name }}</h3>
    </div>
    <br/>
    <div>
      <h3>Email</h3>
      <input
        type="email"
        placeholder="enter your email" 
        v-model="user.email"
      />
      <h3>Your Email:&nbsp;{{ email }}</h3>
    </div>
    <br/>
    <button @click="addUser">Submit</button>
    <br/>
  </form>

  <!-- Users List -->
  <user-list :users="users"/>
  <div>
    <table v-if="user.length" class="w-full bg-white rounded-md">
      <tr>
        <th>
          <h3>Users List</h3>
        </th>
      </tr>
      <tr>
        <td>
          <li v-for="user in users" :key="user">
            <p>
              {{ user.name }}
            </p>
            <p>
              {{ user.email }}
            </p>
          </li>
        </td>
      </tr>
    </table>
  </div>

  <div class="text-3xl font-bold">
    <p v-if="status === 'active'"><h1 :class="true ? 'text-yellow-500' : 'text-green-500'">User is Active</h1></p>
    <p v-else-if="status === 'pending'" :class="true ? 'text-yellow-500' : 'text-blue-500'">User is Pending</p>
    <p v-else :class="active">User is Inactive</p>
  </div>

  <h2>Tasks</h2>
  
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
    <a :href="link"> Let anyone choose status</a>
  </ul>

</template>

