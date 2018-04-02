<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul class="demoUl">
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul class="demoUl">
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
      </li>
    </ul>
    <button @click="clickPhoto">拍照</button>
    <!-- <mt-actionsheet :actions="actionData" v-model="isshow" :cancelText="cancleTxt"></mt-actionsheet> -->
    <mt-popup v-model="isshow" :position="popPos" popup-transition="popup-fade">
      <div class="popContent"> popup 测试使用 </div>
    </mt-popup>
    <!-- <mt-swipe :auto="4000">
      <mt-swipe-item>1</mt-swipe-item>
      <mt-swipe-item>2</mt-swipe-item>
      <mt-swipe-item>3</mt-swipe-item>
    </mt-swipe> -->
    <mt-picker :slots="slotsData" @change="onValueChange" :visibleItemCount="3"></mt-picker>
    <p>当前日期：{{nowDate}}</p>
    <!-- <mt-index-list>
      <mt-index-section index="A">
        <mt-cell title="Aaron"></mt-cell>
        <mt-cell title="Alden"></mt-cell>
        <mt-cell title="Austin"></mt-cell>
        <mt-cell title="Gustin"></mt-cell>
      </mt-index-section>
      <mt-index-section index="B">
        <mt-cell title="Baldwin"></mt-cell>
        <mt-cell title="Braden"></mt-cell>
      </mt-index-section>
      <mt-index-section index="Z">
        <mt-cell title="Zack"></mt-cell>
        <mt-cell title="Zane"></mt-cell>
      </mt-index-section>
    </mt-index-list> -->
    <mt-button plain>plain</mt-button>
    <mt-button icon="back">back</mt-button>
    <mt-button icon="more">更多</mt-button>
    <mt-cell title="标题" label="描述信息" is-link></mt-cell>
    <mt-cell title="标题文字">
      <span>icon 是图片</span>
      <img slot="icon" src="../assets/icon.png" width="24" height="24">
      <p>2018-03-14</p>
    </mt-cell>
  </div>
</template>

<script>
// import { MessageBox } from 'mint-ui'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      isshow: false,
      cancleTxt: '取消上传',
      actionData: [
        {
          name: '拍照0',
          method: function () {
            console.log('000')
          }
        },
        {
          name: '拍照1',
          method: function () {
            console.log('1111')
          }
        },
        {
          name: '拍照2',
          method: function () {
            console.log('22222')
          }
        }
      ],
      popPos: '',
      slotsData: [
        {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot1',
          textAlign: 'center'
        }, {
          divider: true,
          content: '-',
          className: 'slot2'
        }, {
          flex: 1,
          values: ['2015-01', '2015-02', '2015-03', '2015-04', '2015-05', '2015-06'],
          className: 'slot3',
          textAlign: 'center'
        }
      ],
      nowDate: ''
    }
  },
  mounted: function () {
    // MessageBox.prompt('请输入姓名').then(({ value, action }) => {
    //   console.log('确定 ')
    //   console.log(value)
    //   console.log(action)
    // }).catch(err => {
    //   console.log(err)
    // })
  },
  methods: {
    clickPhoto: function () {
      this.isshow = !this.isshow
    },
    onValueChange: function (picker, values) {
      if (values[0] > values[1]) {
        picker.setSlotValue(1, values[0])
      }
      console.log(values)
      this.nowDate = values[0]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
.demoUl {
  list-style-type: none;
  padding: 0;
}
.demoUl li {
  display: inline-block;
  margin: 0 10px;
}
.demoUl a {
  color: #42b983;
}
mt-swipe-item {
  width: 100%;
  height: 100px;
  background-color: #42b983;
  text-align: center;
}
</style>
