<template>
  <div>
    <h1>{{ $page.frontmatter.ListTitle }}</h1>
    <ul class="article-list">
      <li v-for="pageInfo in pagesInfo" 
        class="article-info">
        <h3 class="title"> {{ pageInfo.title }} </h3>
        <hr>
        <div>{{ pageInfo.content }}</div>
        <a v-bind:href="$withBase(pageInfo.path)"
          class="read-more">
          {{ $page.frontmatter.ListReadMore }}
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  computed: {
    pagesInfo() {
      console.log(this.$site.pages);
      let pages = [];
      for (let page of this.$site.pages) {
        if (!page.title) {
          continue;
        }
        if (!page.path || !page.path.match(/^[^_]+$/)) {
          continue;
        }
        let title = page.title;
        let path = page.path;
        let content = "";
        pages.push({
          title,
          path,
          content 
        });
      }
      return pages;
    }
  }
};
</script>

<style lang="stylus">
.article-list 
  margin 0
  padding 0
  .article-info 
    list-style none
    overflow hidden
    box-shadow 3px 3px 15px #555;
    padding: 15px;
    margin: 15px 0;
    border-radius 10px 
    &:after 
      content ""
      clear both
    .title 
      margin: 0;
    .read-more 
      float right
</style>