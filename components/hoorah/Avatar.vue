<script lang="ts" setup>
const props = withDefaults(defineProps<{
  avatar: string;
  width: number;
  height: number;
}>(), {
  avatar: '',
  width: 100,
  height: 100
});
</script>

<template>
  <section class="avatar" :style="{ maxWidth: props.width + 'px', maxHeight: props.height + 'px' }">
    <NuxtImg
        class="avatar__image"
        sizes="100vw sm:50vw md:400px"
        :src="props.avatar"
        :width="'100%'"
        :height="'100%'" />
  </section>
</template>

<style lang="scss" scoped>
.avatar {
  display: inline-flex;
  border-radius: 8px;
  overflow: hidden;
  min-width: 50px;

  &__image {
    object-position: center;
    object-fit: cover;
    width: 100%;
    height: 100%;
  }
}
</style>