<template>
  <div class="editor">
    <div class="editor__md">
      <textarea
        name="markdown"
        :value="content"
        @input="update"
        placeholder="Type your note here ..."
      ></textarea>
    </div>
    <div class="editor__compiled-md">
      <div v-html="compiledMarkdown"></div>
    </div>
  </div>
</template>

<script>
import marked from 'marked';
import _ from 'lodash';

export default {
  props: {
    note: {
      type: String
    }
  },
  computed: {
    compiledMarkdown () {
      return this.content ? marked(this.content) : '';
    },
    content () {
      return this.note;
    }
  },
  methods: {
    update: _.debounce(function (e) {
      this.$emit('note-content-change', e.target.value);
    }, 300)
  }
}
</script>

<style lang="scss" scoped>
@import "../styles/components/notes-create.scss";
</style>