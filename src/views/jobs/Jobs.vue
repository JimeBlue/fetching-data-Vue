<template>
  <div>
    <h1>Jobs</h1>
    <!-- 4) Here instead of showing jobs only if jobs is true,
    we need to say only if jobs.length is true. This is because,
  jobs is an array and it will have a value in the begining, it
won´t be null. -->
    <div v-if="jobs.length">
      <div v-for="job in jobs" :key="job.id" class="job">
        <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
          <h2>{{ job.title }}</h2>
        </router-link>
      </div>
    </div>
    <!-- 5) Else if jobs.length is false, show the message 
    Loading jobs... -->
    <!-- 6) Check if message appears simulating a slow connection,
    go to dev tools > network > No Throttling > GPRS. If it´s not
  there add it. -->
    <div v-else>
      <p>Loading jobs...</p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      jobs: [],
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs")
      .then((res) => res.json())
      .then((data) => (this.jobs = data))
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
