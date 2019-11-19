<template>
  <div class="hello">
    <div>{{ msg }}</div>
    <div v-for="user in users" :key="user.id">
      <p>{{ user.firstname }}</p>
      <p>Id: {{ user.id }}</p>
      <p>
        Age:
        <span>{{ user.age }}</span>
      </p>
    </div>
    <hr />
    <ApolloQuery
      :query="gql => gql`
      query {
        users {
          firstname
        }
      }
      `"
    >
      <template v-slot="{result: {loading, error, data}}">
        <div v-if="data">
          <div>
            <strong>loading :</strong>
            {{ loading }}
          </div>
          <div>
            <strong>data :</strong>
            {{ data }}
          </div>
          <div>
            <strong>error:</strong>
            {{ error }}
          </div>
        </div>
      </template>
    </ApolloQuery>
    <hr />
    <ApolloQuery :query="require('../graphql/users.gql')">
      <template v-slot="{result: {loading, error, data}}">
        <div v-if="data">
          <div>
            <strong>loading :</strong>
            {{ loading }}
          </div>
          <div>
            <strong>data :</strong>
            {{ data }}
          </div>
          <div>
            <strong>error:</strong>
            {{ error }}
          </div>
        </div>
      </template>
    </ApolloQuery>
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
