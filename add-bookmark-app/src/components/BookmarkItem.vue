<template>
  <li>
    <card>
      <div class="card-header">
        <h3>{{title}}</h3>
        <button class="delete-btn" @click="deleteBookmark(id)">Delete</button>
      </div>
      <p>{{description}}</p>
      <a :href="link">View</a>
    </card>
  </li>
</template>

<script>
import Card from './Card.vue';
export default {
  inject: ['deleteBookmark'],
  components: {
    Card
  },
  props: ['id', 'title', 'description', 'link']
}
</script>