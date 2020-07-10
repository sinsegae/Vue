<template>
    <div>
        제목 : <input v-model="title">
        내용 : <input v-model="content">
        <v-btn @click="insertData" v-show="detailIndex === false">추가</v-btn>
        <v-btn @click="updateData" v-show="detailIndex !== false">수정</v-btn>
        <v-btn @click="deleteData" v-show="detailIndex !== false">삭제</v-btn>

        <div>{{ activeItem }}</div>
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
            detailIndex: false
        }
    },
    created(){
        console.log(activeItem)
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
            if(this.title === '' || this.content === ''){
                alert('유효하지 않은 동작입니다.')
                return false
            }
            this.data.splice(this.detailIndex, 1)
            this.title = ''
            this.content = ''
            this.detailIndex = false
        },
        updateData() {
            if(this.title === '' || this.content === ''){
                alert('유효하지 않은 동작입니다.')
                return false
            }
            this.data.splice(this.detailIndex, 1 ,{
                title: this.title,
                content: this.content
            })
            this.title = ''
            this.content = ''
            this.detailIndex = false
        }
    },
    created() {
        this.$on("changeToActive", (index) => {
            this.detailIndex = index
            console.log(this.detailIndex)
            this.title = this.dataOfChild[this.detailIndex].title
            this.content = this.dataOfChild[this.detailIndex].content
        })
    }
}
</script>