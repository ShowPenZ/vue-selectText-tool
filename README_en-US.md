English | [中文](./README.md)

# vue-selectText-tool

> A text select tool component for vue

## Installation

```
$ npm install vue-selectText-tool --save
$ yarn add vue-selectText-tool
```

## Usage
Method 1  Only for the currently inserted selecttext DOM

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
     //This callback gets the corresponding selected information 
     //txt: Selected text, target: The DOM object selected, num: Number of text words selected
     const handler = (txt, target, num) => {
       console.log(txt, target, num);
     };

     return (
       <TextTool.SelectTextTool handler={handler}>
         This is a test text!
       </TextTool.SelectTextTool>
     );
   }
};

```
Method 2  Mount method to the current entire page

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
      //This callback gets the corresponding selected information 
      //txt: Selected text, target: The DOM object selected, num: Number of text words selected
      console.log(txt, target, num);
    }
  },
  render() {
    return <div>This is a test text!</div>;
  }
};
</script>
<style>
</style>

```
# License

MIT

