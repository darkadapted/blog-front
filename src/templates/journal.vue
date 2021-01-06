<template>
    <Layout>
        <div class="journal">
            <div class="container journal-container">
                <div class="journal-header">
                    <h1 class="journal-title">{{$page.strapiJournals.title}}</h1>
                    <div class="journal-meta">
                        <div class="journal-author">
                            <span class="label">Author</span>
                            <span class="author-name">{{$page.strapiJournals.author}}</span>
                        </div>
                        <div class="journal-date">
                            <span class="label">Date</span>
                            <div>{{$page.strapiJournals.date}}</div>
                        </div>
                        <div class="journal-time">
                            <span class="label">Time</span>
                            <span>{{$page.strapiJournals.time}}</span>
                        </div>
                    </div>
                </div>
                <div class="journal-content" v-html="mdToHtml($page.strapiJournals.contents)">
<!--                    <h4 id="use-forestry-as-a-cms-for-gridsome">-->
<!--&lt;!&ndash;                        <g-link href="#use-forestry-as-a-cms-for-gridsome" aria-hidden="true">&ndash;&gt;-->
<!--&lt;!&ndash;                            <span class="icon icon-link"></span>&ndash;&gt;-->
<!--&lt;!&ndash;                        </g-link>&ndash;&gt;-->
<!--                        Use Forestry as a CMS for Gridsome-->
<!--                    </h4>-->
<!--                    <p>-->
<!--                        <a href="https://forestry.io" target="_blank" rel="nofollow noopener noreferrer">Forestry</a>-->
<!--                        is a git-based headless CMS that allows editorial teams to work on Jamstack sites.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        It comes with a slick user interface that empowers editors to edit CommmonMark, YAML, and JSON files.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        Forestry UI was designed by-->
<!--                        <strong>Nichlas W. Andersen</strong>.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        You can import this starter to Forestry and start editing and creating posts or projects right away.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        Forestry also comes with instant previews, for you to preview your content before publishing.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        When you save content in-->
<!--                        <strong>Forestry</strong>,-->
<!--                        it's committed back to your Git repository. If you link your repository to a service like-->
<!--                        <strong>Netlify</strong>-->
<!--                        or-->
<!--                        <strong>Vercel</strong>,-->
<!--                        on every push, your site will be deployed over to a CDN network.-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        Enjoy the best development and user experience! 🚀-->
<!--                    </p>-->
<!--                    <p>-->
<!--                        <g-image  class="img" src="../../static/banana.jpg" />-->
<!--                    </p>-->
            </div>
            </div>
        </div>
    </Layout>
</template>

<page-query>
    query($id: ID!) {
        strapiJournals (id: $id) {
            id
            title
            author
            date
            time
            contents
        }
    }
</page-query>

<script>
    import MarkdownIt from 'markdown-it'
    const md = new MarkdownIt()

    export default {
        name: "journal",
        methods: {
            mdToHtml (content) {
                return md.render(content)
            }
        }
    }
</script>

<style scoped>
    .journal {}
    .container {
        padding: 0 6rem;
    }
    .label {
        display: block;
        font-weight: 700;
        margin-bottom: .5rem;
    }
    h4, h5, h6 {
        font-size: 1.15rem;
    }
    p {
        line-height: 1.5;
        font-size: 1.15rem;
    }
    .journal .journal-container {
        max-width: 840px;
    }
    .journal .journal-container .journal-header {
        padding: 2rem 0 4rem;
    }
    .journal-header .journal-title {
        font-size: 3rem;
        margin: 0 0 4rem;
        padding: 0;
    }
    .journal-header .journal-meta {
        display: flex;
        flex-wrap: wrap;
        font-size: .8rem;
    }
    .journal-meta > div {
        margin-right: 4rem;
    }
    .journal-meta > div:last-of-type {
        margin: 0;
    }
    .img {
        width: 100%;
    }
</style>
