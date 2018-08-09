<template>
  <div>
    <h1>{{msg}}</h1>
    <div class="list-group">
      <div v-for="item in courseList">
        <router-link :to="{name:'detail',params:{id:item.id}}">{{item.name}}</router-link>

  <a href="#" class="list-group-item list-group-item-action flex-column align-items-start">
    <div class="d-flex w-100 justify-content-between">
      <h5 class="mb-1">List group item heading</h5>
      <small class="text-muted">3 days ago</small>
    </div>
    <p class="mb-1">Donec id elit non mi porta gravida at eget metus. Maecenas sed diam eget risus varius blandit.</p>
    <small class="text-muted">Donec id elit non mi porta.</small>
  </a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import qs from 'qs'
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
      // 渲染courseList 通过axios
      var _this = this
      axios.get('http://127.0.0.1:8000/api/v1/course/')
      .then(function (data) {
          // console.log('data.data',data.data.data[1])
          var res = data.data.data
          for (var i = 0; i < res.length; i++) {
            var course_obj = {
              id : res[i].id,
              name : res[i].name,
              img : res[i].course_img,
            }
            _this.courseList.push(course_obj)
          }
          console.log('_this.courseList',_this.courseList)
      })
      .catch(function (err) {
          console.log(err)
      })

      // // 第三版 即第二版(axios)的代替语句 将代码迁移到actions异步中 通过dispatch调用actions异步处理
      // this.$store.dispatch('innitNote')

    },
  }
}
</script>

<style scoped>

</style>
