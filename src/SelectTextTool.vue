<script>
import ClassName from 'classnames';

function selectTextFn(t, fn) {
  t.onmouseup = e => {
    const event = window.event || e;
    const target = event.srcElement ? event.srcElement : event.target;

    if (/input|textarea/i.test(target.tagName) && /firefox/i.test(navigator.userAgent)) {
      const staIndex = target.selectionStart;
      const endIndex = target.selectionEnd;

      if (staIndex !== endIndex) {
        let sText = target.value.substring(staIndex, endIndex);
        sText = sText.replace(/\s*/g, '');

        const num = sText.length;

        fn(sText, target, num);
      }
    } else {
      let sText =
        document.selection === undefined ? document.getSelection().toString() : document.selection.createRange().text;

      if (sText !== '') {
        sText = sText.replace(/\s*/g, '');

        const num = sText.length;

        fn(sText, target, num);
      }
    }
  };
}

const SelectTextTool = {
  name: 'SelectTextTool',
  props: {
    nickName: {
      type: String,
      required: false,
    },
    handler: { type: Function, required: false },
  },
  data() {
    return {};
  },
  mounted() {
    const that = this;
    const { handler } = that;

    selectTextFn(document, handler);
  },
  methods: {},
  render() {
    const that = this;
    const { nickName } = that;

    return <div className={ClassName('Container', nickName)}>{that.$scopedSlots.default()}</div>;
  },
};

export default { SelectTextTool, selectTextFn };
</script>
<style></style>
