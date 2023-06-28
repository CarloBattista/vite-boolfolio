<template>
  <div class="container_projects">
    <div class="rowHeader">
      <h2 class="heading">Projects</h2>
    </div>
    <div class="row_projects">
      <div class="card_project" v-for="(elem, index) in projects" :key="index">
        <div class="wrap_image">
          <img class="image_project" :src="pathApi + '/storage/' + elem.project_images" :alt="elem.title_project + ' Image project'">
        </div>
        <div class="wrap_info">
          <h3 class="info_pr title_pr">{{ elem.title_project }}</h3>
          <h3 class="info_pr client_pr"><span class="off_label">Client:</span> {{ elem.client }}</h3>
          <p class="info_pr desc_pr"><span class="off_label">Description:</span> {{ elem.description_project }}</p>
          <div class="extra_info">
            <h3 class="info_pr title_sec">Technologies used:</h3>
            <span class="tech_label" v-for="(elem, index) in elem.technologies" :key="index">{{ elem.name_technology }},</span>
          </div>
        </div>
      </div>
    </div>
  </div>
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

<style scoped>
.container_projects {
  position: relative;
  width: 100%;
  padding: 3vw 60px;
}

.rowHeader {
  margin-bottom: 12px;
}

.heading {
  color: #fff;
  font-size: 1.2rem;
  font-weight: 500;
}

.row_projects {
  width: 100%;
  display: grid;
  gap: 1.5em;
  grid-template-columns: repeat(5, 1fr);
}

.card_project {
  width: 100%;
  border-radius: 10px;
  aspect-ratio: 9 / 10;
  padding: 1em;
  background: rgba(74, 74, 23, 0.2);
  border: 1px solid rgba(74, 74, 23, 0.5);
  backdrop-filter: blur(3px);
  cursor: pointer;
}

.wrap_image {
  width: 100%;
  aspect-ratio: 16 / 9;
}

.image_project {
  width: 100%;
  height: 100%;
  aspect-ratio: 16 / 9;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  object-fit: cover;
}

.wrap_info {
  margin-top: 10px;
}

.title_pr {
  color: #fff;
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 3px;
}

.client_pr {
  color: #e1e1e1;
  font-size: .8rem;
  font-weight: 400;
  margin-bottom: 3px;
}

.desc_pr {
  color: #e1e1e1;
  font-size: .8rem;
  font-weight: 400;
  margin-bottom: 3px;
}

.off_label{
  color: #aaa;
  font-size: .8rem;
  font-weight: 400;
}

.extra_info{
  margin-top: 1em;
}

.title_sec {
  color: #aaa;
  font-size: .8rem;
  font-weight: 400;
  margin-bottom: 6px;
}

.tech_label{
  color: #e1e1e1;
  font-size: .8rem;
  font-weight: 400;
  margin-right: 6px;
}

.tech_label:last-child{
  margin-right: 0;
}

/* Media Query's */
@media only screen and (max-width: 1100px) {
  .row_projects {
    gap: 1.5em;
    grid-template-columns: repeat(4, 1fr);
  }
}

@media only screen and (max-width: 850px) {
  .row_projects {
    gap: 1.5em;
    grid-template-columns: repeat(3, 1fr);
  }
}

@media only screen and (max-width: 650px) {
  .row_projects {
    gap: 1.5em;
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>