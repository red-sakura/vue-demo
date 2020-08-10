<template>
  <div>
    <img src="@/assets/logo.png">
    <img src="@/assets/timg.jpeg">
    123 456 789
    <div>
      <div id="app">
        {{ test }}
      </div>
      <div v-once>{{ msg }}</div>
      <div>
        <p v-if="seen">现在你看到我了</p>
        <a v-bind:href="url">...</a>
      </div>
      <!-- v-on和v-bind的使用频率非常高,所以提供了缩写方式,v-on省略成@,v-bind省略成: -->
      <div @click="click1">
        <div @click.stop="click2">单击我测试</div>
      </div>
      <button v-on:click="counter += 1">数值:{{ counter }}</button>
      <!--  greet是方法,括号中为方法的参数,这里为实参,在下面methods中的greet的str为形参-->
      <!--  $在内联语句中访问DOM的原始事件,用特殊变量$event(事件变量)将它传入方法 在methods中形参为e  -->
      <!--   dblclick双击   -->
      <button @dblclick="greet('abc',$event)">双击我试试</button>
      <div class="test" v-bind:class="{active: isActive,green: isGreen}"
           style="text-align:center;width: 200px;height: 200px;line-height: 200px;">
        hi vue
      </div>
      <div :style="{color:color2,fontSize:size,background:isRed?'#ff0000':''}">
        hello vue
      </div>
      <div>
        <ol>
          <li v-for="todo in todos">
            {{ todo.text }}
          </li>
        </ol>
      </div>
      <div>
        <ul>
          <li v-for="item,index in items" :key="index">
            {{ index }}{{ item.message }}
          </li>
        </ul>
        <ul>
          <li v-for="value,key in object" :key="key">{{ key }}:{{ value }}</li>
        </ul>
      </div>
      <span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
  </span>
      <div>{{ rawHtml }}</div>
      <div v-html="rawHtml">{{ rawHtml }}</div>
      <div v-bind:class="color">颜色测试</div>
      <div>{{ number + 1 }}</div>
      <div>{{ ok ? 'yes' : 'no' }}</div>
      <div>{{ msg.split('').reverse().join('') }}</div>
      <div>
        <div v-if="type==='A'">A</div>
        <div v-else-if="type==='B'">B</div>
        <div v-else-if="type==='C'">C</div>
        <div v-else>Not A/B/C</div>
      </div>
      <h1 v-show="show">Hello!</h1>
      <hr>
      双向绑定
      <br>
      <div>
        <!--   双向绑定,将输入框中的信息和之后的span中的内容绑定-->
        <input v-model="message1" placeholder="edit me">
        <span>input输入框中的内容是:{{ message1 }}</span><br>
        <textarea v-model="message2" placeholder="edit multiple line"></textarea>
        <p>textarea框中输入的内容为:{{message2}}</p>
        <input type="checkbox" id="jack" value="Jack" v-model="checkNames"><label for="jack">Jack</label>
        <input type="checkbox" id="tom" value="Tom" v-model="checkNames"><label for="tom">Tom</label>
        <input type="checkbox" id="mike" value="Mike" v-model="checkNames"><label for="mike">mike</label>
        <span>选中的名字的数组:{{checkNames}}</span>
        <button type="button" @click="submit">提交</button>
        <br>
        <input type="radio" value="One" id="one" v-model="checkbox"><label for="one">One</label>
        <input type="radio" value="Two" id="two" v-model="checkbox"><label for="two">Two</label>
        <span>选中的数字为:{{checkbox}}</span>
      </div>
      <hr>
      组件的写法 参考 <a>https://blog.csdn.net/FungLeo/article/details/77603537</a>
      <Counter title="title 1:"></Counter>
      组件的复用
      <Counter title="title 2:"></Counter>
      <Counter title="title 3:"></Counter>
      <Counter title="title 4:"></Counter>
    </div>
  </div>

</template>
<script>
// 引用组件
import Counter from './counter.vue'
export default {
  name: 'demo',
  components: {Counter},
  data () {
    return {
      message: '页面加载于 ' + new Date().toLocaleString(),
      test: '测试',
      seen: false,
      todos: [
        {text: '学习 JavaScript'},
        {text: '学习 Vue'},
        {text: '整个牛项目'}
      ],
      msg: '一次性插值',
      rawHtml: '<span style="color: blue">this is should be blue</span>',
      color: 'yellow',
      number: 2,
      ok: 1,
      url: 'www.baidu.com',
      isActive: false,
      isGreen: true,
      color2: '#0000ff',
      size: '100px',
      isRed: true,
      type: 'D',
      show: true,
      items: [
        {message: 'Foo'},
        {message: 'Bar'}
      ],
      object: {
        title: 'hello',
        author: 'MuKun',
        publishTime: '2020-08-10'
      },
      counter: 0,
      // 双向绑定用到的属性,可以设置默认值
      message1: '',
      message2: '',
      checkNames: ['Tom'],
      checkbox: 'Two'
    }
  },
  methods: {
    click1: function () {
      alert('事件冒泡')
    },
    click2: function () {
      alert('阻止事件冒泡')
    },
    greet: function (str, e) {
      alert('Hello')
      // 这里的this指的是data? 弹出的数据是size的值100px
      alert(this.size)
      alert(str)
      console.log(e)
    },
    submit: function () {
      console.log(this.checkNames)
      // eslint-disable-next-line no-unused-vars
      var postObj = {
        msg1: this.message1,
        msg2: this.message2,
        checkVal: this.checkbox
      }
      console.log(postObj)
    }
  }
}
</script>

<style scoped>
#app {
  font-size: larger;
  color: red
}

.green {
  color: green
}

.yellow {
  color: yellow;
  font-size: 100px
}

.active {
  background-color: aqua;
}

.test {
  font-size: 60px;
}
</style>
