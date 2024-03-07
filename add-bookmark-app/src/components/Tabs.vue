<template>
  <div class="header-tabs">
    <button @click="setSelectedTab('bookmarks')" :class="bkmrksBtnMode">My Bookmarks</button>
    <button @click="setSelectedTab('add-bookmark')" :class="addBkmrksBtnMode">Add Bookmark</button>
  </div>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import Bookmarks from './Bookmarks.vue';
import AddBookmark from './AddBookmark.vue';
export default {
  components: {
    Bookmarks,
    AddBookmark
  },
  data() {
    return {
      selectedTab: 'bookmarks',
      bookmarksList: [
        {
          id: 'google',
          title: 'Google',
          description: 'web search',
          link: 'https://www.google.com/'
        }
      ]
    }
  },
  provide() {
    return {
      bookmarks: this.bookmarksList,
      addBookmark: this.addBookmark,
      deleteBookmark: this.deleteBookmark
    }
  },
  computed: {
    bkmrksBtnMode() {
      return this.selectedTab === 'bookmarks' ? 'active' : null
    },
    addBkmrksBtnMode() {
      return this.selectedTab === 'add-bookmark' ? 'active' : null
    }
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addBookmark(title, description, link) {
      const newBookmark = {
        id: new Date().toISOString,
        title: title,
        description: description,
        link: link
      };
      this.bookmarksList.push(newBookmark);
      this.selectedTab = 'bookmarks';
    },
    deleteBookmark(bookmarkId) {
      const index = this.bookmarksList.findIndex(bookmark => bookmark.id === bookmarkId);
      this.bookmarksList.splice(index, 1);
    }
  }
}
</script>