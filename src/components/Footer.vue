<template>
    <div>
        제목 : <input v-model="title">
        내용 : <input v-model="content">
        <v-btn @click="insertData" v-show="detailIndex === null">추가</v-btn>
        <v-btn @click="updateData" v-show="detailIndex !== null">수정</v-btn>
        <v-btn @click="deleteData" v-show="detailIndex !== null">삭제</v-btn>
        <v-btn @click="cancle" v-show="detailIndex !== null">취소</v-btn>
    </div>
</template>

<script>
export default {
    props: {
        dataOfChild : Array,
        activeItem : Number
    },
    data() {
        return {
            data: this.dataOfChild,
            title: "",
            content: "",
            detailIndex: null
        }
    },
    methods: {
        insertData() {
            if(this.title === "" || this.content === "") {
                alert('제목 또는 내용이 누락되었습니다.')
                return false
            }
            this.data.unshift({
                    title: this.title,
                    content: this.content
                })
                this.title = ''
                this.content = ''
        },
        deleteData() {
            this.data.splice(this.detailIndex, 1)
            this.title = ''
            this.content = ''
            this.detailIndex = null
            this.$emit("revertToActive", null)
        },
        updateData() {
            this.data.splice(this.detailIndex, 1 ,{
                title: this.title,
                content: this.content
            })
            this.title = ''
            this.content = ''
            this.detailIndex = null
            this.$emit("revertToActive", null)
            console.log(this.activeItem)
        },
        cancle() {
            this.title = ''
            this.content = ''
            this.detailIndex = null
        }
    },
    watch: {
        activeItem: function() {
            if(this.activeItem === null) {
                return false
            }
            console.log(this.activeItem)
            this.detailIndex = this.activeItem
            this.title = this.dataOfChild[this.detailIndex].title
            this.content = this.dataOfChild[this.detailIndex].content
        }
    }
}
</script>