<template>
  <div>
    <h1>Jobs</h1>
    <div v-for="job in jobs" :key="job.id" class="job">
      <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </router-link>
    </div>
  </div>
</template>
<!-- EXPLANATION: instead of using the data from our
components, we´re going to fetch data from an API.
We´re going to use a service called json server,
which simulates an API to which we can make requests to.
Json server allows us to use a json file containing data
as a database resource with various different endpoints.
 -->
<!-- 1) In the root of the project, create a data folder,
inside it create the db.json file. In this file, include 
the data you want in json format. Note: in json files, any
top level keys are called resources. In our case, jobs
is a resource. -->
<!-- 2) Install the json server package locally inside this project: 
npm install json-server -->
<!-- 3) To watch our db.json file, we run 
  npx json-server --watch + the path of our json file: data/db.json.
So, run  npx json-server --watch data/db.json -->
<!-- 4) After running the watch command, we´ll get 
a local port with the end point /jobs to get the jobs
resource we have in the db.json file. So, when we open
the local port in a browser, it´s going to send a get
request for the jobs resouce and it´s going to send 
back json with all the different objects included in 
the jobs resource-->
<!-- IMPORTANT: if you want to see how to get and post data
in a real database, not an API, go to repo 
vuejs-playlist-vue2-basics-continue-CLI, branches: 
posting to firebase and retrieving blogs from firebase-->
<script>
export default {
  data() {
    return {
      jobs: [
        { title: "Ninja UX Designer", id: 1, details: "lorem" },
        { title: "Ninja Web Developer", id: 2, details: "lorem" },
        { title: "Ninja Vue Developer", id: 3, details: "lorem" },
      ],
    };
  },
};
</script>

<style>
.job h2 {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer;
  color: #444;
}
.job h2:hover {
  background: #ddd;
}
.job a {
  text-decoration: none;
}
</style>
