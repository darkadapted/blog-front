<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
<!--    <g-image alt="Example image" src="~/favicon.png" width="135" />-->
    <div class="home-content">
      <div class="home-title">
        <h1 class="title">Simplicity.Aesthetics.Value.</h1>
        <h2 class="subtitle">Hi there, I'm an independent Digital Designer & Art Director focused on digital design for brands that like to have fun.</h2>
      </div>
      <div class="projects">
        <div class="project" v-for="project in $page.projects.edges" :key="project.node.id">
          <g-link :to="`projects/${project.node.id}`" class="project-link">
            <g-image class="img" alt="Example image" :src="`http://106.75.254.31:1337${project.node.cover.url}`" />
            <h3 class="project-title">{{project.node.title}}</h3>
            <div class="categories">
              <span class="category" v-for="tag in project.node.tags" :key="tag.id">{{tag.tag}}</span>
            </div>
          </g-link>
        </div>
      </div>
    </div>
    <div >
      <div class="latest-journals-heading container">
        <span class="label">Latest and greatest</span>
      </div>
      <div class="latest-journals">
        <div class="container">
          <g-link :to="`journal/${journal.node.id}`" class="journal" v-for="journal in $page.journals.edges" :key="journal.node.id">
            <h3 class="journal-title">
              {{journal.node.title}}
            </h3>
          </g-link>
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
  query {
    projects: allStrapiProjects {
      edges {
        node {
          id
          title
          content
          cover {
            url
          }
          tags {
            id
            tag
          }
        }
      }
    }
    journals: allStrapiJournals {
      edges {
        node {
          id
          title
        }
      }
    }
  }
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  name: 'home'
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
.home-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 6rem;
}
.home-title {
  text-align: center;
  width: 480px;
  max-width: 100%;
  margin: 0 auto;
  padding: 4rem 0 8rem;
}
.home-title .title {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0 0 2rem;
  word-break: break-word;
}
.home-title .subtitle {
  font-size: 1.15em;
  font-weight: 400;
  line-height: 1.68;
  opacity: .6;
}
.projects {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 4rem;
}
.projects .project:nth-child(3n+1)  {
  grid-column: auto/span 2;
}
.projects .project .project-link {
  text-decoration: none;
  text-align: center;
}
.project .project-link .img {
  width: 100%;
  height: 560px;
  -o-object-fit: cover;
  object-fit: cover;
  transition: all .15s ease;
  box-shadow: 0 0 40px -20px rgba(0,0,0,.25);
}
.project .project-link .img:hover {
  transform: scale(1.1);
}
.project .project-title {
  font-size: 1rem;
  color: rgba(0, 0, 0, 0.99);
  margin: 2rem 0 1rem;
}
.project .project-link .categories {
  font-size: .8rem;
  color: rgba(0, 0, 0, 0.99);
}
.project-link .categories .category {
  margin-right: .8rem;
}
.latest-journals-heading {
  margin-top: 6rem;
  margin-bottom: 1rem;
  font-size: .6rem;
  font-weight: 400;
  text-transform: uppercase;
}
.latest-journals-heading .label {
  display: block;
  font-weight: 700;
  margin-bottom: .5rem;
}
.latest-journals {
  margin: 0;
  border-left: 0;
  border-right: 0;
  border-top: 1px solid #f3f3f3;
  border-bottom: 1px solid #f3f3f3;
}
.latest-journals .container{
  display: flex;
  flex-wrap: wrap;
}
.latest-journals .container .journal{
  text-decoration: none;
  color: black;
  width: 21.5%;
  padding: 12px;
}

.latest-journals .container .journal:first-child,
.latest-journals .container .journal:nth-child(2),
.latest-journals .container .journal:nth-child(3)  {
  border: 0;
  border-right: 1px solid #f3f3f3;
}
.journal[data-v-460714ac]:first-child, .journal[data-v-460714ac]:nth-child(2) {
  border-bottom: 1px solid #f3f3f3;
}
.latest-journals .journal .journal-title {
  font-size: 1rem;
  line-height: 1.35;
  word-break: break-word;
}
</style>
