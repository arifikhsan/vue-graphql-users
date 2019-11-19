# vue-graph-try

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

```html
<template>
  <div class="graphql-test">
    {{ getAllUsers }}
  </div>
</template>

<script>
  import { GET_ALL_USERS_QUERY } from "../graphl/queries/userQueries";
  export default {
    name: "GraphQL-Test",
    apollo: {
      getAllUsers: {
        query: GET_ALL_USERS_QUERY
      }
    }
  };
</script>
```

https://stackabuse.com/building-graphql-apis-with-vue-js-and-apollo-client/
