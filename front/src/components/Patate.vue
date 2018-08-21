<template>
<h1 class="Patate">{{ msg }}</h1>
</template>

<script>
export default {
  name: "Patate",
  props: {},
  created: function() {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchData();
  },
  data: function() {
    return {
      msg: "Before server answers"
    };
  },
  watch: {
    // call again the method if the route changes
    $route: "fetchData"
  },
  methods: {
    fetchData: function() {
      var myHeaders = new Headers();
      myHeaders.append("Content-Type", "text/plain");
      var getUsers = new Request("http://localhost:3000/users", {
        method: "GET",
        headers: myHeaders,
        mode: "cors",
        cache: "default"
      });
      fetch(getUsers)
        .then((response) => {
          response.json().then((data) => {
            this.msg = data.test;
          });
        })
        .catch(console.log);
    }
  }
};
</script>