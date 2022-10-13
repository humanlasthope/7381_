<template>
 <div class="jwchat">
  <!--
Text String-"" in v-model input box
taleList session content Array-[]
toolConfig toolbar to configure Object-{}
width JwChat box width string-750px
height JwChat box height string-570px
config component configuration Object-{}
scrollType message automatically to low String scroll noroll
showRightBox Boolean false true
winBarConfig Multi-window configuration
quickList automatically matches quick replies
@enter The raw data entered for the event that was triggered when the input box was clicked to send or enter
@clickTalk Clicks the user and nickname in the chat box column to trigger the event current conversation data
       -->
  <JwChat-index
  width="890px"
   v-model="inputMsg"
   :taleList="taleList"
   :config="config"
   :showRightBox="true"
   scrollType="scroll"
   :winBarConfig="winBarConfig"
   :quickList="config.quickList"
   @enter="bindEnter"
   @clickTalk="talkEvent"
  >
   <!-- Window right sidebar -->
   <JwChat-rightbox :config="rightConfig" @click="rightClick" /></JwChat-index>
 </div>
</template>
<script>
const img = 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
const listData = [
  {
    date: 'Sat 8 Oct 10:08am',
    text: {
      text: 'Hi'
    },
    mine: false,
    name: 'LL',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
  },
  {
    date: '',
    text: { text: 'Play game?' },
    mine: false,
    name: 'Xiaochuan Sun',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
  },
  {
    text: 'Sat 8 Oct 10:08am',
    type: 'tip'
  },
  {
    date: 'Sat 8 Oct 10:08am',
    text: {
      text: 'Good Morning'
    },
    mine: false,
    name: 'Xiaochuan Sun',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
  },
  {
    date: '2Sat 8 Oct 10:08am',
    text: { text: "<img data-src='" + img + "'/>" },
    mine: false,
    name: 'Xiaochuan Sun',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
  },
  {
    date: 'Sat 8 Oct 10:08am',
    text: {
      text:
    'Hello!'
    },
    mine: true,
    name: 'Xiaochuan Sun',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
  },
  {
    date: 'Sat 8 Oct 10:08am',
    mine: false,
    name: 'Peace&Love',
    img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
    text: {
      text:
    'Hi'
    }
  }
]
function getListArr (size) {
  const listSize = listData.length
  if (!size) {
    size = listSize
  }
  const result = []
  for (let i = 0; i < size; i++) {
    const item = listData[(Math.random() * listSize) >> 0]
    item.id = Math.random().toString(16).substr(-6)
    result.push(item)
  }
  return result
}
export default {
  components: {},
  data () {
    return {
      // 输入框中的文字
      inputMsg: '',
      // 会话内容
      taleList: [],
      // 工具栏配置
      tool: {
        show: ['file', 'history', 'img', ['文件1', '', '美图']],
        showEmoji: true
      },
      // 组件配置
      config: {
        img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
        name: 'JwChat',
        dept: 'Game and Keep Fit',
        callback: this.bindCover,
        historyConfig: {
          show: true,
          tip: 'The prompt displayed when scrolling to the top',
          callback: this.bindLoadHistory
        },
        // 自动匹配快捷回复
        quickList: [
          { text: 'This is jwchat. What questions do you want to know?', id: 3 },
          { text: 'jwchat is the best chat component', id: 4 },
          { text: 'Play Game and Keep Fit', id: 5 },
          { text: 'Play Game and Keep Fit', id: 6 },
          { text: 'Play Game and Keep Fit', id: 7 },
          { text: 'Play Game and Keep Fit', id: 8 },
          { text: 'Play Game and Keep Fit', id: 10 },
          { text: 'Play Game and Keep Fit', id: 11 },
          {
            text: 'Play Game and Keep Fit',
            id: 12
          },
          {
            text: ' Play Game and Keep Fit',
            id: 13
          }
        ]
      },
      // 多个窗口配置
      winBarConfig: {
        active: 'win01', // 当前选中窗口
        width: '160px', // 窗口宽度大小
        listHeight: '60px', // 窗口单个高度
        // 用户列表
        list: [
          {
            id: 'win00',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            name: 'Lao Ba',
            dept: 'Game and Keep Fit',
            readNum: 1
          },
          {
            id: 'win01',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            name: 'Xiaochuan Sun',
            dept: 'Lorem ipsum dolor sit amet consectetur',
            readNum: 12
          },
          {
            id: 'win02',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            name: 'SS',
            dept: 'Last words to say',
            readNum: 12
          },
          {
            id: 'win03',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            name: 'LL',
            dept: 'newbee',
            readNum: 0
          },
          {
            id: 'win04',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            name: 'Sun',
            dept: 'The official customer service'
          }
        ],
        callback: this.bindWinBar
      },
      // 窗口右边栏配置
      rightConfig: {
        tip: 'Please chat civilly.',
        // notice:
        //   'Notice: This is a highly free chat component developed on AVue, Vue, Element-ui.',
        listTip: 'Online Now',
        list: [
          {
            name: 'Lao Ba',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2',
            id: 1
          },
          {
            id: 2,
            name: 'Xiaochuan SUN',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
          },
          {
            id: 3,
            name: 'Sun',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
          },
          {
            id: 4,
            name: 'LL',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
          },
          {
            name: 'SS',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
          }
        ]
      },
      // 快捷回复配置
      talk: [
        'Auto Reply1',
        'Auto Reply2',
        'Auto Reply3',
        'Auto Reply4',
        'Auto Reply5',
        'Auto Reply6'
      ],
      quickConfig: {
        nav: ['Auto Reply', 'Prompt reply'],
        showAdd: true,
        maxlength: 200,
        showHeader: true,
        showDeleteBtn: true
      },
      rightConfig2: {
        listTip: 'Online Now',
        // notice: 'Notice:This is a highly free chat component developed on AVue, Vue, Element-ui.',
        list: [
          {
            name: 'Lao Ba',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
          },
          {
            name: 'LL',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
            // https://img1.baidu.com/it/u=31094377,222380373&fm=26&fmt=auto&gp=0.jpg
          },
          {
            name: 'SS',
            img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
            // https://img1.baidu.com/it/u=2109725846,3376113789&fm=26&fmt=auto&gp=0.jpg
          }
        ]
      }
    }
  },
  methods: {
  // Switch the user window to load the corresponding history
    bindWinBar (play = {}) {
      const { type, data = {} } = play
      console.log(play)
      if (type === 'winBar') {
        const { id, dept, name, img } = data
        this.config = { ...this.config, id, dept, name, img }
        this.winBarConfig.active = id
        if (id === 'win00') {
          this.taleList = getListArr()
        } else this.taleList = getListArr((Math.random() * 4) >> 0)
      }
      if (type === 'winBtn') {
        const { target: { id } = {} } = data
        const { list } = this.winBarConfig
        this.winBarConfig.list = list.reduce((p, i) => {
          if (id !== i.id) p.push(i)
          return p
        }, [])
      }
    },
    // Clicking the user and nickname in the chat box column triggers the event
    talkEvent (play) {
      console.log(play)
    },
    // Send or Enter events triggered when the input box is clicked
    bindEnter (e) {
      console.log(e)
      const msg = this.inputMsg
      if (!msg) return
      const msgObj = {
        date: '2020/05/20 23:19:07',
        text: { text: msg },
        mine: true,
        name: 'JwChat',
        img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
      }
      this.taleList.push(msgObj)
    },
    // 快捷回复，组件点击选中事件
    bindTalk (play) {
      console.log('talk', play)
      const { key, value } = play
      if (key === 'navIndex' && value === '1') {
        this.talk = ['Rely1', 'Reply2', 'Reply3']
      }
      if (key === 'navIndex' && value === '2') {
        this.talk = ['Prompt reply1', 'Prompt reply2', 'Prompt reply3']
      }
      if (key === 'select') {
        this.inputMsg = value
        // this.bindEnter()
      }
      if (key === 'delIndex') {
        this.talk.splice(value, 1)
      }
    },
    /**
   * @description: 点击加载更多的回调函数
   * @param {*}
   * @return {*}
   */
    bindLoadHistory () {
      const history = new Array(3).fill().map((i, j) => {
        return {
          date: '2020/05/20 23:19:07',
          text: { text: j + new Date() },
          mine: false,
          name: 'JwChat',
          img: 'https://images.pexels.com/photos/4014919/pexels-photo-4014919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2'
        }
      })
      const list = history.concat(this.list)
      this.taleList = list
      console.log('Loading...', list, history)
    },
    /**
   * @description:
   * @param {*} type The currently clicked button
   * @param {*} plyload 附加文件或者需要处理的数据
   * @return {*}
   */

    bindCover (event) {
      console.log('header', event)
    },
    rightClick (type) {
      console.log('rigth', type)
    },

    eddText () {
      this.$nextTick(() => {
        const btn = document.querySelector('.web__msg-submit')
        const input = document.querySelector('.web__msg-input')
        const innerbox = document.querySelector('.el-input__inner')
        console.log(btn)
        console.log(input)
        input.placeholder = 'Text Here'
        btn.innerHTML = 'Send'
        btn.style.background = 'purple'
        innerbox.placeholder = 'Search'
      })
    }
  },
  created () {
    this.eddText()
  },
  mounted () {
    this.taleList = getListArr()
  }
}
</script>

  <style>
.jwchat {
 /* height: 1200px; */
 /*font-family: sans-serif;*/
 text-align: center;
 color: grey;
  margin-left: 150px;
  margin-bottom: 20px;
}
.wrapper .notice{
  display: none;
}
.ChatPage .header[data-v-177d6428]{
  z-index:1000;
  background-color: #523e7a;
}
/*
Reference:
“JWChat,” JwChat. [Online]. Available: https://codegi.gitee.io/jwchatdoc/. [Accessed: 14-Oct-2022].-->
“Vue - 聊天框功能（JwChat）,” Vue - 聊天框功能（JwChat）_Jie_1997的博客-CSDN博客_jwchat使用. [Online]. Available:
https://blog.csdn.net/Jie_1997/article/details/120154717?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522166568097616800192274509%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&amp;request_id=166568097616800192274509&amp;biz_id=0&amp;utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-120154717-null-null.142%5Ev56%5Econtrol%2C201%5Ev3%5Eadd_ask&amp;utm_term=jwchat&amp;spm=1018.2226.3001.4187. [Accessed: 14-Oct-2022].
*/
</style>
