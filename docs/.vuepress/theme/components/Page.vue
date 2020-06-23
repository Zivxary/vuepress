<template>
  <main class="page">
    <slot name="top" />

    <div class="theme-default-content" >
      <ListPage v-if="page_type == 'list'"/>
      <Content  v-else/>
    </div>

    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <slot name="bottom" />
  </main>
</template>

<script>
import PageEdit from '@theme/components/PageEdit.vue'
import PageNav from '@theme/components/PageNav.vue'
import ListPage from '@theme/components/ListPage.vue'

export default {
  components: { PageEdit, PageNav, ListPage },
  props: ['sidebarItems'],
  computed: {
    page_type() {
      return this.$page.frontmatter.PageType
    },
  }
};
</script>

<style lang="stylus">
@require '../styles/wrapper.styl'

.page
  padding-bottom 2rem
  display block

</style>
