<template>
  <div>
    <div>
      <div>

        <div>
          <span>구분</span>
          <div>
            <span>메시지ID:</span><input type="text" v-model="searchInfo.msgId">
          </div>
        </div>

        <div>
          <span>결과코드</span>
          <div>
            <span class="radio-type"><input type="radio" name="result" v-model="searchInfo.resultCode" id="resultAll" value="All"><label for="AresultAll">전체</label></span>
            <span class="radio-type"><input type="radio" name="result" v-model="searchInfo.resultCode" id="resultSu" value="Y"><label for="resultSu">성공</label></span>
            <span class="radio-type">
              <input type="radio" name="result" v-model="searchInfo.resultCode" id="resultFa" value="N">
              <label for="resultFa">실패</label>
              <input type="text" placeholder="실패코드를 입력하세요." v-model="searchInfo.failCode" :disabled="searchInfo.resultCode != 'N'">
            </span>
          </div>
        </div>

        <div>
          <span>메시지 처리 상태</span>
          <div>
            <span class="radio-type"><input type="radio" name="msgStat" v-model="searchInfo.msgStatus" id="statAll" value="All"><label for="statAll">전체</label></span>
            <span class="radio-type"><input type="radio" name="msgStat" v-model="searchInfo.msgStatus" id="statSu" value="Y"><label for="statSu">성공</label></span>
            <span class="radio-type"><input type="radio" name="msgStat" v-model="searchInfo.msgStatus" id="statFa" value="N"><label for="statFa">실패</label></span>
          </div>
        </div>

        <div>
          <span>이통사</span>
          <div>
            <span class="radio-type"><input type="radio" name="agency" v-model="searchInfo.agencySel" id="All" value="All"><label for="All">전체</label></span>
            <span class="radio-type"><input type="radio" name="agency" v-model="searchInfo.agencySel" id="KT" value="KT"><label for="KT">KT</label></span>
            <span class="radio-type"><input type="radio" name="agency" v-model="searchInfo.agencySel" id="SKT" value="SKT"><label for="SKT">SKT</label></span>
            <span class="radio-type"><input type="radio" name="agency" v-model="searchInfo.agencySel" id="LGU+" value="LGU+"><label for="LGU+">LGU+</label></span>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchInfo : {
        msgId : '',
        resultCode : 'All',
        failCode : '',
        msgStatus : 'All',
        agencySel : 'All',
      }
    }
  },
  watch : {
    "searchInfo.resultCode"(newVal){
      if(newVal != 'N') {
        this.searchInfo.failCode = '';
      }
    }
  }
}
</script>