<template>
  <h1>{{ a }}</h1>
  <editor-content :editor="editor" v-model="state.text" />

  <bubble-menu :editor="editor" :tippy-options="{ duration: 100 }" v-if="editor" class="popover">
    <button @click="editor.chain().focus().toggleBold().run()" :class="getClass('bold')">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        aria-hidden="true"
        role="img"
        class="iconify iconify--ic"
        width="20"
        height="20"
        preserveAspectRatio="xMidYMid meet"
        viewBox="0 0 20 20"
      >
        <path
          fill="currentColor"
          d="M15.6 10.79c.97-.67 1.65-1.77 1.65-2.79c0-2.26-1.75-4-4-4H7v14h7.04c2.09 0 3.71-1.7 3.71-3.79c0-1.52-.86-2.82-2.15-3.42zM10 6.5h3c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5h-3v-3zm3.5 9H10v-3h3.5c.83 0 1.5.67 1.5 1.5s-.67 1.5-1.5 1.5z"
        ></path>
      </svg>
    </button>
    <button @click="editor.chain().focus().toggleItalic().run()" :class="getClass('italic')">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        aria-hidden="true"
        role="img"
        class="iconify iconify--ic"
        width="20"
        height="20"
        preserveAspectRatio="xMidYMid meet"
        viewBox="0 0 20 20"
      >
        <path fill="currentColor" d="M10 4v3h2.21l-3.42 8H6v3h8v-3h-2.21l3.42-8H18V4h-8z"></path>
      </svg>
    </button>
    <button @click="editor.chain().focus().toggleStrike().run()" :class="getClass('strike')">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        aria-hidden="true"
        role="img"
        class="iconify iconify--ic"
        width="20"
        height="20"
        preserveAspectRatio="xMidYMid meet"
        viewBox="0 0 20 20"
      >
        <path
          fill="currentColor"
          d="M7.24 8.75c-.26-.48-.39-1.03-.39-1.67c0-.61.13-1.16.4-1.67c.26-.5.63-.93 1.11-1.29a5.73 5.73 0 0 1 1.7-.83c.66-.19 1.39-.29 2.18-.29c.81 0 1.54.11 2.21.34c.66.22 1.23.54 1.69.94c.47.4.83.88 1.08 1.43s.38 1.15.38 1.81h-3.01c0-.31-.05-.59-.15-.85c-.09-.27-.24-.49-.44-.68c-.2-.19-.45-.33-.75-.44c-.3-.1-.66-.16-1.06-.16c-.39 0-.74.04-1.03.13s-.53.21-.72.36c-.19.16-.34.34-.44.55c-.1.21-.15.43-.15.66c0 .48.25.88.74 1.21c.38.25.77.48 1.41.7H7.39c-.05-.08-.11-.17-.15-.25zM21 12v-2H3v2h9.62c.18.07.4.14.55.2c.37.17.66.34.87.51s.35.36.43.57c.07.2.11.43.11.69c0 .23-.05.45-.14.66c-.09.2-.23.38-.42.53c-.19.15-.42.26-.71.35c-.29.08-.63.13-1.01.13c-.43 0-.83-.04-1.18-.13s-.66-.23-.91-.42c-.25-.19-.45-.44-.59-.75s-.25-.76-.25-1.21H6.4c0 .55.08 1.13.24 1.58s.37.85.65 1.21c.28.35.6.66.98.92c.37.26.78.48 1.22.65c.44.17.9.3 1.38.39c.48.08.96.13 1.44.13c.8 0 1.53-.09 2.18-.28s1.21-.45 1.67-.79c.46-.34.82-.77 1.07-1.27s.38-1.07.38-1.71c0-.6-.1-1.14-.31-1.61c-.05-.11-.11-.23-.17-.33H21V12z"
        ></path>
      </svg>
    </button>
  </bubble-menu>

  <floating-menu :editor="editor" :tippy-options="{ duration: 100 }" v-if="editor">
    <FloatBtnVue />
  </floating-menu>
</template>

<script setup>
import FloatBtnVue from "./FloatBtn.vue";
import { reactive } from "vue";
import { useEditor, EditorContent, BubbleMenu, FloatingMenu } from "@tiptap/vue-3";
import StarterKit from "@tiptap/starter-kit";

const editor = useEditor({
  content: "<p>I’m running Tiptap with Vue 3 🎉</p><p>This is a test and fun</p><p></p>",
  extensions: [StarterKit],
});

const getClass = (type) => {
  if (!editor || !editor.value) return "";
  return editor.value.isActive(type) ? "is-active" : "";
};

const state = reactive({ text: "" });
const a = "TipTap with Ghost like look and feel - WYSIWYG (Minimal)";
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html,
body {
  background: #ebf1f5;
  font-family: Inter, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Helvetica Neue, Arial, Noto Sans,
    sans-serif;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 700px;
  margin: 0 auto;
  background: #fff;
}

.popover {
  background-color: #32383f;
  color: #fff;
  position: relative;
  display: inline-flex;
  align-items: center;
  box-shadow: 0 0 1px rgb(0 0 0 / 5%), 0 5px 18px rgb(0 0 0 / 8%);
  border-radius: 0.5rem;
}

.popover button {
  flex: 1;
  padding: 5px 7.5px;
  outline: none;
  border: none;
  background: transparent;
  color: inherit;
  box-shadow: none;
  line-height: inherit;
  height: 30px;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  border-right: 1px solid #eee;
}

.popover button.is-active {
  color: green;
}

.popover button:last-child {
  border-right: 1px solid transparent;
}

.popover:after {
  position: absolute;
  top: 30px;
  left: calc(50% - 8px);
  width: 0;
  border-top: 8px solid #32383f;
  border-right: 8px solid transparent;
  border-left: 8px solid transparent;
  content: "";
  font-size: 0;
  line-height: 0;
  transition: left 0.06s ease;
}

h1 {
  text-align: center;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  height: 50px;
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

pre {
  word-wrap: break-word;
}

.ProseMirror {
  height: calc(100vh - 50px);
  border: none;
  outline: none;
  padding: 1rem;
}

p {
  margin: 0.75em 0;
}

ul,
ol {
  margin-left: 2rem;
}

li p {
  margin: 0;
}
</style>
