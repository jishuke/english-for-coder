<template>
  <div class="search-container">
    <div class="logo">
      <img alt="Vue logo" src="../assets/logo.png">
    </div>
    <div class="search-wrapper">
      <div class="logo-search">
        <img alt="Vue logo" src="../assets/logo.png">
        <el-input class="search-inp" :clearable="true" v-model="input" placeholder="请输入单词查询" @keyup.enter.native="search">
          <el-button slot="append" icon="el-icon-search" @click="search"></el-button>
        </el-input>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex'
export default {
  name: 'Search',
  data() {
    return {
      input: ''
    }
  },
  computed: {
    ...mapGetters(['keyWord'])
  },
  methods: {
    search() {
      this.setKeyWord(this.input)
    },
    ...mapMutations({
      setKeyWord: 'SET_KEYWORD'
    })
  }
}
</script>

<style lang="scss" scoped>
@import '@/common/css/variable.scss';
.search-container {
  margin-top: 60px;
  .logo img {
    width: 300px;
  }
  .search-wrapper {
    display: flex;
    justify-content: center;
    position: relative;
  }
  .logo-search {
    width: 50%;
    display: flex;
    img {
      height: 40px;
      margin-right: 20px;
      display: none;
      // opacity: 0;
    }
  }
}
</style>
