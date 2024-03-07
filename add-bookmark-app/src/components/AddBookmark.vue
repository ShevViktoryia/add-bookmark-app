<template>
  <card>
    <form @submit.prevent="submitForm">
      <div class="form-fields">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleField">
      </div>
      <div class="form-fields">
        <label for="description">Description</label>
        <textarea name="description" id="description" rows="5" ref="descrField"></textarea>
      </div>
      <div class="form-fields">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkField">
      </div>
      <button type="submit" class="form-btn">Add bookmark</button>
    </form>
  </card>
</template>

<script>
export default {
  inject: ['addBookmark'],
  methods: {
    submitForm() {
      const title = this.$refs.titleField.value;
      const description = this.$refs.descrField.value;
      const link = this.$refs.linkField.value;

      this.addBookmark(title, description, link);
    }
  }
}
</script>

