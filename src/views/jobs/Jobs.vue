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
<script>
export default {
  data() {
    return {
      /* 4)Create a jobs array to store data fetched 
      from API */
      jobs: [],
    };
  },
  /* 1) The data will be fetched inside the mouted cycle hook */
  mounted() {
    /* 2) Use the fetch API to fetch the data, passing with fetch
    the endpoint provided by json server for fetching the jobs */
    fetch("http://localhost:3000/jobs")
      .then((res) => res.json())
      /* 3) Put the data we fetched inside the jobs array */
      .then((data) => (this.jobs = data))
      /* 5) Use catch block, which will fire a function
      if there is an error, and we get that 
      error back as an argument inside this function.
      Here I console log the error message */
      /* 6) Next steps in JobDetails component */
      .catch((err) => console.log(err.message));
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
