<script setup lang="ts">
const props = withDefaults(defineProps<{
  availability: boolean;
}>(), {
  availability: false
});
</script>

<template>
  <section class="availability" :class="{ 'availability--available': props.availability }">
    {{ props.availability ? 'Disponible' : 'Indisponible' }}
  </section>
</template>

<style scoped lang="scss">
.availability {
  display: inline;
  padding: 0.25rem 0.5rem 0.25rem 1.5rem;
  border-radius: 10px;

  &--available {
    background: #d4f6c5;
    position: relative;

    &::before {
      position: absolute;
      display: flex;
      align-items: center;
      justify-content: center;
      content: '';
      width: 0.5rem;
      height: 0.5rem;
      background: #4caf50;
      border-radius: 50%;
      top: calc(50% - 0.25rem);
      left: 0.5rem;
    }
  }

  :not(&--available) {
    background: #f6c5c5;
    position: relative;

    &::before {
      position: absolute;
      display: flex;
      align-items: center;
      justify-content: center;
      content: '';
      width: 0.5rem;
      height: 0.5rem;
      border-radius: 50%;
      background: #ec5a5a;
      top: calc(50% - 0.25rem);
      left: 0.5rem;
    }
  }
}
</style>