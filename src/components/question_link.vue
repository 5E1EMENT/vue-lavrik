<template>
    <div id="question_link" class="container">
        <h2>{{question}}</h2>
        <hr>
        <ul>
            <li>
                <input type="radio" value="a" id="a" v-model="answer_link">
                <label for="a">a</label>
            </li>

            <li>
                <input type="radio" value="div" id="div" v-model="answer_link">
                <label for="div">div</label>
            </li>
            <li>
                <input type="radio" value="span" id="span" v-model="answer_link">
                <label for="span">span</label>
            </li>
            <li>
                <input type="radio" value="img" id="img" v-model="answer_link">
                <label for="img">img</label>
            </li>

        </ul>
        <hr>
        <button class="btn btn-success" @click="link_done">Next</button>

    </div>
</template>

<script>
    export default {
        name: "question_link",
        data() {
            return {
                answer_link: 'a',
                question: 'Какой тег задает ссылку?'
            }
        },
        methods: {
            link_done() {
                let al = {
                    question: this.question,
                    answer: this.answer_link
                }
                this.$emit('link', al)
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