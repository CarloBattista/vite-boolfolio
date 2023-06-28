<template>
  <div>Projects</div>
</template>

<script>
import axios from 'axios';

export default {
  name: "ProjectsComp",
  data() {
    return {
      projects: [],
      pathApi: "http://127.0.0.1:8000/api",
    }
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects() {
      axios.get(`${this.pathApi}/projects`)
        .then(res => {
          this.projects = res.data.projects
          console.log(res.data)
        })
    },
  }
}
</script>

<style scoped></style>