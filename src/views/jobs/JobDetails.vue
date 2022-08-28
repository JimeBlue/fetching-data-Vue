<template>
  <div>
    <!-- 11) Output the content of a specific job.
    This may give an error, because we set job to
  null to beginn with. See the solution in the next
branch: conditionally showing data -->
    <h1>{{ job.title }}</h1>
    <p>The job id is {{ id }}</p>
    <p class="job-id">{{ job.details }}</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      /* 10) Create the data property to store a specific job.
      Initially it will be null, but once we get the data back
      from the server this will be a javascript object. */
      job: null,
    };
  },
  /* 7) Inside mounted(), fetch specific job with a specific id */
  mounted() {
    /* 8) Use the endpoint for all jobs + the id. The id we
    have, because we accepted as a prop. So we just say this.id */
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => res.json())
      /* 9) Store the data, i.e the specific job with the
      specific id, inside the data property */
      .then((data) => (this.job = data))
      /* 10) Catch error */
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
.job-id {
  text-align: center;
}
</style>
