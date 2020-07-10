<template>
    <div>
        <h2>List</h2>
        <table style="width:100%">
            <colgroup>
                <col width="20%">
                <col width="auto">
            </colgroup>
            <thead>
                <th>제목</th>
                <th>내용</th>
            </thead>
            <tbody style="text-align:center">
                <tr v-for="(value, index) in dataOfChild" :key="index" @click="activeToItem(index)">
                    <td>{{ value.title }}</td>
                    <td>{{ value.content }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    props: ['dataOfChild', 'changeToActive'],
    data() {
        return {

        }
    },
    methods: {
        activeToItem(index) {
            this.$emit("changeToActive", index)
        }
    }
}
</script>