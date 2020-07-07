<template>
    <div>
        <v-text-field
            label="제목"
            v-model="title"
        ></v-text-field>
        <v-text-field
            label="내용"
            v-model="content"
        ></v-text-field>
        <v-btn @click="add">추가</v-btn>
    </div>
</template>

<script>
import read_data from '../data/read_data.js'

export default {
    data() {
        return {
            data: read_data,
            title: "",
            content: ""
        }
    },
    methods: {
        add() {
            if(this.title !== "" && this.content !== "") {
                this.data.unshift({
                    title: this.title,
                    content: this.content
                })
                this.title = ''
                this.content = ''
            } else {
                alert('제목 또는 내용이 누락되었습니다.')
            }
        }
    }
}
</script>