<template>
  <div>
    <editor-content :editor="editor" />
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { Editor, EditorContent } from '@tiptap/vue-3';
import StarterKit from '@tiptap/starter-kit';

export default {
  components: {
    EditorContent,
  },
  setup() {
    const editor = ref(null);

    onMounted(() => {
      editor.value = new Editor({
        extensions: [StarterKit],
        content: '<p>Hello World!</p>',
      });
    });

    onBeforeUnmount(() => {
      if (editor.value) {
        editor.value.destroy();
      }
    });

    return {
      editor,
    };
  },
};
</script>

<style>
/* Add any custom styles for the editor here */
</style>
