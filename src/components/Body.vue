<template>
    <div>
        <h2>List</h2>
        <select v-model="select">
            <option value="all">전체</option>
            <option value="title">제목</option>
            <option value="content">내용</option>
        </select>
        <input v-on:input="search" :value="keyword">
        <v-btn @click="reset">Reset</v-btn>
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
                <tr v-for="(value, index) in dataOfChild" :key="index" 
                @click="activeToItem(index)" 
                v-show="select === 'all' ? value.title.includes(keyword) || value.content.includes(keyword) : select === 'title' ? value.title.includes(keyword) : value.content.includes(keyword)">
                        <td >{{ value.title }}</td>
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
        keyword: "",
        select: 'all'
      }
    },
    watch: {
      "select"(newVal){
        console.log(this.select)
      }
    },
    methods: {
        activeToItem(index) {
            this.$emit("changeToActive", index)
        },
        search: function(e) {
            this.keyword = e.target.value
        },
        reset(){
          this.keyword = '';
          this.select.state = '전체';
        }
    }
}
</script>`