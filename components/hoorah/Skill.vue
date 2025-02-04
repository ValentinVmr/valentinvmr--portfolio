<script lang="ts" setup>
const props = defineProps<{
  skill: string;
}>();
</script>

<template>
  <section class="skill">
    <p class="skill__text">
      {{ props.skill }}
    </p>
  </section>
</template>

<style lang="scss" scoped>
.skill {
  box-sizing: border-box;
  display: inline-flex;
  background-color: #ECF3F4;
  border-radius: 4px;
  padding: 0.25rem 0.5rem;

  &__text {
    color: #035266;
    font-weight: 400;
    text-wrap: nowrap;
  }
}
</style>