<script setup>
  defineProps({
    width: String,
    height: String,
    iconColor: String,
  })
</script>

<template>
    <svg
      :width="width" 
      :height="height" 
      viewBox="0 0 18 18" 
      role="presentation"
    >
      <g :fill="iconColor">
        <slot />
      </g>
    </svg>
</template>

  
<style scoped>
  svg {
    display: inline-block;
    vertical-align: baseline;
    margin-bottom: -2px; /* yes, I'm that particular about formatting */
  }
</style>