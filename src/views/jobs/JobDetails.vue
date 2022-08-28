<template>
  <div>
    <h1>Job Details</h1>
    <p class="job-id">The job id is {{ id }}</p>
  </div>
</template>

<script>
export default {
  props: ["id"],
};
</script>

<style>
.job-id {
  text-align: center;
}
</style>
