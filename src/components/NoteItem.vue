<template>
  <div class="notes__item">
    <h4>{{ title }}</h4>
    <p class="note-body">{{ body }}</p>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    body: {
      type: String
    }
  }
}
</script>

<style scoped>
.notes__item {
  border-bottom: 1px solid #585f75;
  margin-bottom: 10px;
  padding: 10px;
  font-size: 0.83rem;
  text-align: left;
}

.notes__item h4 {
  font-weight: bold;
  font-size: 1rem;
  margin: 0 0 10px 0;
  padding: 0;
}

.notes__item p {
  margin: 0;
  padding: 0;
}

.note-body {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>