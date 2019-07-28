
<template>
  <div class="article-container">
    <div v-html="toHtml" class="markdown-body"></div>
    <div class="comments">
      <div class="comments-item">
        <div class="comment-top">
          <div class="comment-left">
            <div class="block"><el-avatar shape="square" :size="40" src="/imgs/avatar.jpg"></el-avatar></div>
            <div class="username">垃圾</div>
          </div>
          <div class="comment-right time">2019/7/28 15:25</div>
        </div>
        <div class="comment-content">
          做的还可以加油
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import marked from "marked";
// marked.setOptions({
//   renderer: new marked.Renderer(),
//   highlight: function(code) {
//     return require('highlight.js').highlightAuto(code).value;
//   },
//   pedantic: false,
//   gfm: true,
//   breaks: false,
//   sanitize: false,
//   smartLists: true,
//   smartypants: false,
//   xhtml: false
// });

export default {
  data() {
    return {
      toHtml: "",
      data: `Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned |  |
| col 2 is      | centered      |    |
| zebra stripes | are neat      |     |`
    };
  },
  methods: {},
  mounted() {
    this.toHtml = marked(this.data);
  }
};
</script>

<style lang='scss'>
@import "@/assets/css/github-markdown.css";
.markdown-body {
  box-sizing: border-box;
  min-width: 200px;
  max-width: 980px;
  margin: 0 auto;
  padding: 45px;
  background-color: #fff;
  
}
.comments{
    margin-top: 30px;
    .comments-item{
      background-color: #fff;
      // border: 1px solid #000;
      border-radius: 5px;
      font-size: 13px;
      .comment-top{
        color: #606266;
        display: flex;
        justify-content: space-between;
        padding: 10px;
        align-items: center;
        border-bottom: 3px solid #000;
        .comment-left{
          display: flex;
          align-items: center;
          .block{
            margin-right: 10px;
          }
        }
        .time{
          
          	
        }
      }
      .comment-content{
        padding: 30px;
        color: #303133;
        font-size: 14px;
      }
    }
  }

@media (max-width: 767px) {
  .markdown-body {
    padding: 15px;
  }
}
</style>
