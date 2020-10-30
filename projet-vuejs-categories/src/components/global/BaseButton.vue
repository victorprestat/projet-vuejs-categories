<template>
  <button class="bg-blue-500 text-white font-bold py-2 px-4 rounded hover:bg-blue-700">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "base-button",
  props: ['text']
}
</script>