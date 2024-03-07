<template>
  <dialog open>
    <div>
      <slot>
        <h2>{{ title }}</h2>
      </slot>
    </div>
  </dialog>
</template>

<script>
export default {
  props: ['title']
}
</script>