<template>
  <div class="hello">
    <div>{{ msg }}</div>
    <div v-for="user in users" :key="user.id">
      <h1>{{ user.firstname }}</h1>
      <h2>Id: {{ user.id }}</h2>
      <h3>Age: <span>{{ user.age }}</span></h3>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  apollo: {
    users: gql`
      query {
        users {
          id
          firstname
          age
        }
      }
    `
  }
};
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
