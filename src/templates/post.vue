<template>
    <Layout>
        <div class="project">
            <div class="container">
                <div class="project-header">
                    <h1 class="project-title">
                        {{$page.project.title}}
                    </h1>
                    <div class="project-info">
                        <div class="categories-container">
                            <div class="categories">
                                <span class="label">Categories</span>
                                <span class="category" v-for="tag in $page.project.tags" :key="tag.id">{{tag.tag}}</span>
                            </div>
                        </div>
                        <div class="year-container">
                            <span class="label">Year</span>
                            <div>2019</div>
                        </div>
                    </div>
                </div>
                <div class="content">

                </div>
            </div>
            <div class="content" v-html="mdToHtml($page.project.contents)">
<!--                <p>-->
<!--                    The&nbsp;-->
<!--                    <strong>{{$page.project.title}}</strong>-->
<!--                    &nbsp;fruits grow from a&nbsp;-->
<!--                    <strong>banana</strong>-->
<!--                    &nbsp;blossom in hanging clusters, also called a bunch or&nbsp;-->
<!--                    <strong>banana</strong>-->
<!--                    stem. The fruits grow in rows called tiers or hands. There can be as many as twenty fruits to a hand, and as many as twenty tiers in a bunch. A bunch usually weighs between 30 and 50 kilograms (65 to 110 pounds).-->
<!--                </p>-->
<!--                <p>-->
<!--                    <g-image style="max-width: 100%" :src="`localhost:1337${$page.project.cover.url}`"></g-image>-->
<!--                </p>-->
            </div>
            <div class="content">
                <p><g-image style="max-width: 100%" :src="`http://106.75.254.31:1337${this.$page.project.cover.url}`"></g-image></p>
            </div>
        </div>
    </Layout>
</template>

<page-query>
    query($id: ID!) {
       project: strapiProjects (id: $id) {
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
            contents
        }
    }
</page-query>

<script>
    import MarkdownIt from 'markdown-it'
    const md = new MarkdownIt()

    export default {
        name: "post",
        methods: {
            mdToHtml (content) {
                return md.render(content)
            }
        }
    }
</script>

<style scoped>
    .project {
    }
    .project .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 0rem;
    }
    .project .container .project-header {
        padding: 0 0 15vh 0rem;
    }
    .container .project-header .project-title {
        font-size: 4rem;
        margin: 0 0 4rem;
        padding: 0;
    }
    .container .project-header .project-info {
        display: flex;
        flex-wrap: wrap;
        font-size: .8rem;
    }
    .project-info .categories-container {
        margin-right: 4rem;
    }
    .categories-container .categories .category::after {
        content: ", ";
    }
    .categories-container .categories .category:last-of-type::after {
        content: "";
    }
    .project-info .year-container {
        margin-right: 4rem;
    }
    .label {
        display: block;
        font-weight: 700;
        margin-bottom: .5rem;
    }
    .project .content {

    }
</style>
