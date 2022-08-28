<template>
  <div>
    <!-- EXPLANATION: now we can´t see any specific job,
    bacause job.title is causing an error. In the console
  we get "TypeError: Cannot read properties of null (reading 'title')"".
This happends because we set job to be null initially. So, it
takes seconds to get the data from the API. Therefore, title or
any other property inside job is not available. To solve that 
I have to output any property inside job, after the fetch 
request has completed and we have a value in job, insted of null -->
    <!-- 1) Output only if job is true, i.e. only if job has a value.
    That will happend after the fetch is completed -->
    <div v-if="job">
      <h1>{{ job.title }}</h1>
      <p>Job id: {{ id }}</p>
      <p>{{ job.details }}</p>
    </div>
    <!-- 2) Else,if job is false, i.e the data is not loaded, show the message
    "Loading job details..." -->
    <div v-else>
      <p>Loading job details...</p>
    </div>
    <!-- 3) Do the same in the Jobs component. Next steps
    in that componet-->
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      job: null,
    };
  },

  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      .then((data) => (this.job = data))
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
.job-id {
  text-align: center;
}
</style>
