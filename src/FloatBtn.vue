<template>
  <button class="float-btn">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      aria-hidden="true"
      role="img"
      class="iconify iconify--mdi"
      width="32"
      height="32"
      preserveAspectRatio="xMidYMid meet"
      viewBox="0 0 24 24"
    >
      <path fill="currentColor" d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2Z"></path>
    </svg>
  </button>
</template>

<script setup></script>

<style scoped>
.float-btn {
  margin-left: -4rem;
  margin-top: -1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40px;
  width: 40px;
  border-radius: 50%;
  outline: none;
  border: none;
  cursor: pointer;
  box-shadow: 0 4px 8px #aaaaaa;
  color: #777;
  background-color: #eee;
  overflow: hidden;
}
:hover {
  color: #222;
  background-color: #ccc;
}
</style>
