<template>
  <li>
    <card>
      <div class="card-header">
        <h3>{{title}}</h3>
        <button>Delete</button>
      </div>
      <p>{{description}}</p>
      <a :href="link">View</a>
    </card>
  </li>
</template>

<script>
import Card from './Card.vue';
export default {
  components: {
    Card
  },
  props: ['title', 'description', 'link']
}
</script>