<template>
  <ul>
    <bookmark-item
    v-for="item in bookmarks"
    :key="item.id"
    :id="item.id"
    :title="item.title"
    :description="item.description"
    :link="item.link"
    ></bookmark-item>
  </ul>
</template>

<script>
import BookmarkItem from './BookmarkItem.vue';
export default {
  inject: ['bookmarks'],
  components: {
    BookmarkItem
  }
}
</script>