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
    }
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects() {
      axios.get('http://127.0.0.1:8000/api/projects')
        .then(res => {
          this.projects = res.data.projects
          console.log(res.data)
        })
    },
  }
}
</script>

<style scoped></style>