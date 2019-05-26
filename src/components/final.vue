<template>
    <div class="container">
        <h2>Итого</h2>
        <hr>
        <table class="table">
            <thead>
                <th>Вопрос</th>
                <th>Ответ</th>
            </thead>
            <tbody>
                <tr v-for="(answer, index) in answers" :key="index">
                    <td>{{answer.question}}</td>
                    <td>{{answer.answer}}</td>
                </tr>
            </tbody>
        </table>

    </div>
</template>

<script>
    export default {
        name: "final",
        props: ['answers'],
        data() {
            return {
            }
        }
    }
</script>

<style scoped>
    table {
        margin: auto
    }
</style>