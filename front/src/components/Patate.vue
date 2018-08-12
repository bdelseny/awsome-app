<template>
<h1>{{ msg }}</h1>
</template>

<script>
export default {
  name: "Patate",
  props: {},
  computed: {
    msg: function() {
      var myHeaders = new Headers();
      myHeaders.append("Content-Type", "text/plain");
      var getUsers = new Request("http://localhost:3000/users", {
        method: "GET",
        headers: myHeaders,
        mode: "cors",
        cache: "default"
      });
      fetch(getUsers).then(console.log);
    }
  }
};
</script>