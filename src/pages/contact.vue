<template>
    <Layout>
        <div class="container">
            <div class="contact-header">
                <h1 class="contact-title">Say hi!</h1>
                <p>
                    Leave me a note with any questions you might have, I'll get back to you as soon as possible.
                </p>
            </div>
            <form name="contact" class="contact-form">
                <div class="sender-info">
                    <div>
                        <label for="name" class="label">Your name</label>
                        <input type="text" name="name" v-model="user.username">
                    </div>
                    <div>
                        <label for="email" class="label">Your email</label>
                        <input type="email" name="email" v-model="user.email">
                    </div>
                </div>
                <div class="message">
                    <label for="message" class="label">Message</label>
                    <textarea name="message" v-model="user.message"></textarea>
                </div>
                <button class="button" @click.prevent="onSubmit">Submit form</button>
            </form>
        </div>
    </Layout>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "contact",
        data() {
            return {
                user: {
                    username: '',
                    email: '',
                    message: ''
                }
            }
        },
        methods: {
           async onSubmit() {
               try {
                 const { data } = await axios({
                       method: 'POST',
                       url: 'http://localhost:1337/contact-Infos',
                       data: {...this.user}
                 })
                   alert('success')
               }catch (e) {
                   console.log('data', data)
                   alert('error: email must be a valid email')
               }
            }
        }
    }
</script>

<style scoped>
    .container {
        padding: 0 6rem;
    }
    p {
        line-height: 1.5;
        font-size: 1.15rem;
    }
    .container .contact-header {
        padding: 2rem 0 4rem;
    }
    .container .contact-header .contact-title {
        font-size: 4rem;
        margin: 0 0 4rem;
        padding: 0;
    }
    .container .contact-form .sender-info {
        display: flex;
        flex-wrap: wrap;
        margin-bottom: 2rem;
    }
    .sender-info>div {
        flex: 1;
        margin-right: 4rem;
    }
    .label {
        display: block;
        font-weight: 700;
        margin-bottom: .5rem;
    }
    input, textarea {
        background: transparent;
        border: 1px solid #f3f3f3;
        outline: none;
        border-radius: .3rem;
        padding: .8rem 1rem;
        color: inherit;
        font-size: 1rem;
        width: 100%;
    }
    .button {
        color: #fff;
        background: #000;
        outline: none;
        border: 0;
        font-size: .8rem;
        padding: .8rem 1.6rem;
        border-radius: .3rem;
        margin-top: 2rem;
        cursor: pointer;
        transition: opacity .25s ease;
        letter-spacing: .035em;
    }
</style>
