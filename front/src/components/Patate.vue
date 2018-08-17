<template>
<h1>{{ msg }}</h1>
</template>

<script>
export default {
  name: "Patate",
  props: {},
  created() {
    // fetch the data when the view is created and the data is
    // already being observed
    this.msg = this.fetchData();
  },
  watch: {
    // call again the method if the route changes
    $route: "fetchData"
  },
  methods: {
    fetchData() {
      this.msg = "Method called";
      var that = this;
      var myHeaders = new Headers();
      myHeaders.append("Content-Type", "text/plain");
      var getUsers = new Request("http://localhost:3000/users", {
        method: "GET",
        headers: myHeaders,
        mode: "cors",
        cache: "default"
      });
      return fetch(getUsers)
        .then(response => {
          response.json().then(function(data) {
            console.log(data.test);
            return data.test;
          });
        })
        .catch(console.log);
      // replace `getPost` with your data fetching util / API wrapper
      // getPost(this.$route.params.id, (err, post) => {
      //   this.loading = false;
      //   if (err) {
      //     this.error = err.toString();
      //   } else {
      //     this.post = post;
      //   }
      // });
    }
  }
};
</script>