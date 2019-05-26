<template>
    <div id="question_link" class="container">
        <h2>{{question}}</h2>
        <hr>
        <ul>
            <li>
                <input type="checkbox" value="a" id="a" v-model="answer_inline">
                <label for="a">a</label>
            </li>

            <li>
                <input type="checkbox" value="div" id="div" v-model="answer_inline">
                <label for="div">div</label>
            </li>
            <li>
                <input type="checkbox" value="span" id="span" v-model="answer_inline">
                <label for="span">span</label>
            </li>
            <li>
                <input type="checkbox" value="img" id="img" v-model="answer_inline">
                <label for="img">img</label>
            </li>

        </ul>
        <hr>
        <button class="btn btn-success" @click="inline_done">Next</button>

    </div>
</template>

<script>
    export default {
        name: "question_inline",
        data() {
            return {
                question: 'Какие из этих тегов строчные?',
                answer_inline: []
            }
        },
        methods: {
            inline_done() {
                let al = {
                    question: this.question,
                    answer: this.answer_inline
                }
                this.$emit('inline', al)
            }
        }
    }
</script>

<style scoped>
    #question_link {
        text-align: left;
    }
    ul {
        list-style-type: none;
        padding: 0;

    }
    li {
        text-align: left;
    }

    input {
        display: inline;
        margin-right: 10px;
    }
</style>