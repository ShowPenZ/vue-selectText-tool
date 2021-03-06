[English](https://github.com/ShowPenZ/vue-selectText-tool/blob/master/README_en-US.md) | 中文

# vue-selectText-tool

> 一个vue的选择文字组件

## Installation

```
$ npm install vue-selectText-tool --save
$ yarn add vue-selectText-tool
```

## Usage
用法1 仅针对当前插入的SelectText dom

``` vue
<script>
import TextTool from "vue-selectText-tool";

 export default {
   name: "SelectTextTool",
   data() {
     return {};
   },
   methods: {},
   render() {
     //这个回调拿到相应被选择的信息 
     //txt: 选择的文本, target: 被选择的dom对象, num: 选择的文本字数
     const handler = (txt, target, num) => {
       console.log(txt, target, num);
     };

     return (
       <TextTool.SelectTextTool handler={handler}>
         这是一个测试 文本!
       </TextTool.SelectTextTool>
     );
   }
};

```
用法2 挂载方法到当前整个页面

``` vue
import TextTool from "vue-selectText-tool";

export default {
  name: "SelectTextTool",
  data() {
    return {};
  },
  mounted() {
    const that = this;

    TextTool.selectTextFn(document, that.handler);
  },
  methods: {
    handler(txt, target, num) {
      //这个回调拿到相应被选择的信息 
      //txt: 选择的文本, target: 被选择的dom对象, num: 选择的文本字数
      console.log(txt, target, num);
    }
  },
  render() {
    return <div>这是一个测试 文本!</div>;
  }
};
</script>
<style>
</style>

```
# License

MIT
