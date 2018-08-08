<template>
  <div>
    <h1>{{msg}}</h1>
    <div>
      <div v-for="item in courseList">
        <router-link :to="{name:'detail',params:{id:item.id}}">{{item.name}}</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "course",
  data() {
    return {
      msg: '这是课程',
      courseList: []
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    init() {
      // this.courseList = [
      //   {id: 1, name: '21天学会Python', img: ''},
      //   {id: 2, name: '21天学会Java', img: ''},
      //   {id: 3, name: '21天学会Linux', img: ''},
      //   {id: 4, name: '21天学会大数据', img: ''},
      // ]

      // 第二版(axios) 已迁移到store的actions中以便统一异步操作
      var _this = this
      axios.get('http://127.0.0.1:8000/api/v1/course/')
      .then(function (data) {
          console.log('init axios',data)
          _this.$store.commit('initNoteList',data.data)
      })
      .catch(function (err) {
          console.log(err)
      })

      // // 第三版 即第二版(axios)的代替语句 将代码迁移到actions异步中 通过dispatch调用actions异步处理
      this.$store.dispatch('innitNote')
    },
  }
}
</script>

<style scoped>

</style>
