<template>
    <div id="app" class="container">
        <div class="questions ">
            <qlink @link="answer_check($event)" v-if="first"></qlink>
            <qinline @inline="answer_check($event)" v-else-if="second"></qinline>
            <final v-else :answers="answers"></final>
        </div>
    </div>
</template>

<script>
    import qlink from './components/question_link'
    import qinline from './components/question_inline'
    import final from './components/final'

    export default {
        name: 'app',
        data() {
            return {
                first: true,
                second: true,
                answers: []

            }
        },
        methods: {
            answer_check(e) {
                let value = {
                    question: e.question,
                    answer: e.answer
                };
                this.answers.push(value)
                this.first = !this.first;
                if (this.first) {
                    this.second = !this.second
                    this.first = !this.first;
                }


            }


        },
        computed: {},
        components: {
            qlink,
            qinline,
            final
        }
    }
</script>

<style>
    #app {
        text-align: center;
    }

    .questions {
        display: block;
        margin: 0 auto;
    }
</style>
