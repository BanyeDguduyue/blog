<template>
  <div class="article-container">
    <div class="article-item" v-for="(item,idx) in articlelist" :key="idx">
      <h1 class="title">{{item.title}}</h1>
      <div class="article-info">
        <div>
          作者:
          <span class="info-ipt">{{item.author}}</span>
        </div>
        <div>
          时间:
          <span class="info-ipt">{{item.time}}</span>
        </div>
        <div>
          阅读:
          <span class="info-ipt">{{item.read}}</span>
        </div>
        <div>
          评论:
          <span class="info-ipt">{{item.comments}}</span>
        </div>
      </div>
      <div class="article-msg">{{item.content}}</div>
      <nuxt-link
        :to="{path:`/article`}"
        class="whole-article"
        @click="handlereadarticle(item.idx)"
      >阅读全文</nuxt-link>
    </div>
    <div>
      <nuxt-child></nuxt-child>
    </div>
    <div class="article-item">
      <h1 class="title">什么是HTML5?</h1>
      <div class="article-info">
        <div>
          作者:
          <span class="info-ipt">半夜的孤独月</span>
        </div>
        <div>
          时间:
          <span class="info-ipt">2019-7-24 17:04</span>
        </div>
        <div>
          阅读:
          <span class="info-ipt">0</span>
        </div>
        <div>
          评论:
          <span class="info-ipt">12</span>
        </div>
      </div>
      <div class="article-msg">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe expedita assumenda ullam neque! Culpa sint porro facere nisi nam, consequatur deleniti. Aliquid quos ipsa facilis, sint molestias doloribus praesentium dolor.
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe expedita assumenda ullam neque! Culpa sint porro facere nisi nam, consequatur deleniti. Aliquid quos ipsa facilis, sint molestias doloribus praesentium dolor.
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Saepe expedita assumenda ullam neque! Culpa sint porro facere nisi nam, consequatur deleniti. Aliquid quos ipsa facilis, sint molestias doloribus praesentium dolor.
      </div>
      <button class="whole-article">阅读全文</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["articlelist", "currenttype"],
  methods: {}
};
</script>

<style lang="scss">
.article-container {
  .article-item {
    background-color: #fff;
    padding: 30px 60px;
    margin-bottom: 20px;
    .title {
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 10px;
      color: #303133;
      text-align: center;
    }
    .article-info {
      font-size: 14px;
      font-weight: 400;
      display: flex;
      justify-content: center;
      margin-bottom: 20px;
      div {
        margin-left: 10px;
        .info-ipt {
          color: #409eff;
        }
      }
    }
    .article-msg {
      // padding: 0 30px;
      text-indent: 20px;
      text-align: justify;
      line-height: 22px;
      margin-bottom: 20px;
      color: #606266;
    }
    .whole-article {
      border: none;
      outline: none;
      padding: 5px 10px;
      background-color: rgb(236, 168, 9);
      background-color: #409eff;
      color: white;
      cursor: pointer;
    }
  }
}
</style>
