<template>
    <Layout>
        <div class="container">
            <div class="journal-hero">
                <h1 class="journal-header">
                    a wise person once said...
                </h1>
            </div>
            <g-link class="journal-post" v-for="journal in $page.journals.edges" :key="journal.node.id" style="text-decoration: none; " :to="`journal/${journal.node.id}`">
                <div class="container journal">
                    <h2 class="journal-title">
                        {{journal.node.title}}
                    </h2>
<!--                    <p class="journal-excerpt">-->
<!--                        Get up and running with Forestry CMS, a git-backed headless CMS with a slick editing interface.-->
<!--                    </p>-->
                </div>
            </g-link>
        </div>
    </Layout>
</template>

<page-query>
    query {
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
        name: "journal"
    }
</script>

<style scoped>
    .container {
        padding: 0 0rem;
    }
    .container .journal-hero {
        padding: 4rem 0;
        text-align: center;
        color: #f3f3f3;
    }
    .container .journal-hero .journal-header {
        font-size: 3rem;
        font-weight: 700;
        padding: 0;
        margin: 0;
    }
    .journal-post {
        padding: 2rem 0;
        display: block;
        text-decoration: none;
        transition: background .5s ease;
        margin: 0;
    }
    .journal-post .container {
        padding: 0 6rem;
    }
    .journal-post .journal {
        max-width: 720px;
        transition: transform .5s ease;
    }
    .journal-post .journal:hover {
        transform: translateX(10%);
    }
    .journal-post .journal .journal-title {
        font-size: 2rem;
        color: #000;
    }
</style>
