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
                <tr v-for="(value, index) in data" :key="index">
                    <td>{{ value.title }}</td>
                    <td>{{ value.content }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import read_data from '../data/read_data.js'

export default {
    data() {
        return {
            data: read_data
        }
    }
}
</script>