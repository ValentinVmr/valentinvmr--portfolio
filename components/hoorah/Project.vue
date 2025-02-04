<script lang="ts" setup>
const props = withDefaults(defineProps<{
  name: string;
  description: string;
  image: string;
  link?: string;
  github?: string;
  inProgress?: boolean;
  backgroundColor?: string;
}>(), {
  name: '',
  description: '',
  image: '',
  link: '',
  github: '',
  inProgress: false,
  backgroundColor: 'transparent'
});
</script>

<template>
  <section class="project">
    <aside class="image" :style="{ backgroundColor: props.backgroundColor }">
      <NuxtImg :src="props.image" :alt="'Image du projet ' + name" width="250" height="250"/>
      <span v-if="props.inProgress" class="image__in-progress">En cours</span>
    </aside>
    <article class="project__description">
      <h3>{{ props.name }}</h3>
      <p>{{ props.description }}</p>
      <nav class="links">
        <a class="link" v-if="props.link" :href="props.link">
          <IconLink class="link" />
        </a>
        <a class="link" v-if="props.github" :href="props.github">
          <IconGithub class="link" />
        </a>
      </nav>
    </article>
  </section>
</template>

<style lang="scss">
.link {
  width: 1.5rem;
  height: 1.5rem;
}

.links {
  display: flex;
  gap: 0.5rem;
}

.project {
  box-sizing: content-box;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  border: 1px solid #d5dbdc;
  border-radius: 8px;
  height: 100%;
  box-shadow: 0 10px 30px 5px rgba(0, 0, 0, 0.11);
  transition: transform 0.2s ease;

  &:hover {
    transform: translateY(-0.25rem);

  }

  &__description {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    flex: 1;
    padding: 0.5rem 1rem;
  }

  .image {
    position: relative;
    width: 100%;
    aspect-ratio : 1 / 1;

    &__in-progress {
      position: absolute;
      bottom: 0;
      right: 0;
      background-color: rgba(255, 255, 255, 0.34);
      color: white;
      padding: 0.25rem 0.5rem;
      border-top-left-radius: 8px;
    }

    img {
      border-top-left-radius: 8px;
      border-top-right-radius: 8px;
      object-position: center;
      width: 100%;
      height: 100%;
    }
  }

  article {
    h3 {
      font-size: 1.25rem;
      margin: 0;
    }

    p, a {
      color: #637587;
    }

    p {
      flex: 1;
    }


  }
}
</style>