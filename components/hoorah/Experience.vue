<script setup lang="ts">
const props = withDefaults(defineProps<{
  company: string;
  position: string;
  startDate: string;
  endDate: string;
  description: string;
  skills: string[];
  city: string;
  companyImage: string;
}>(), {
  company: '',
  position: '',
  startDate: '',
  endDate: 'aujourd\'hui',
  description: '',
  city: '',
  companyImage: '',
});
</script>
<template>
<section class="xp">
  <article class="xp-info">
    <div class="xp-dates-and-location">
      <span class="dates">{{ props.startDate }} - {{ props.endDate }}</span>
      <span class="location">
        <IconLocation class="location-icon" /> {{ props.city }}
      </span>
    </div>
    <div class="xp-company-and-position">
      <NuxtImg class="xp-company-image" :src="props.companyImage" :alt="'Logo de ' + props.company" width="64" height="64"/>
      <div class="xp-company-and-position__info">
        <span class="xp-position">{{ props.position }}</span>
        <span class="xp-company">{{ props.company }}</span>
      </div>
    </div>
  </article>
  <article class="xp-description">
    <p v-html="props.description"></p>
    <ul>
      <li v-for="skill in (props.skills || [])">
        <HoorahSkill :skill="skill"/>
      </li>
    </ul>
  </article>
</section>
</template>

<style lang="scss" scoped>
.xp {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
}

.location-icon {
  width: 0.75rem;
  height: 0.75rem;
}

.xp-info {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  flex-wrap: wrap;
  flex: 0 0 100%;
}

.xp-dates-and-location {
  display: flex;
  flex-wrap: nowrap;
  gap: 0.75rem;

  .dates {
    color: #47516B;
    text-wrap: nowrap;
  }

  .location {
    display: flex;
    align-items: baseline;
    gap: 0.25rem;
    color: #79819A;

    & > svg {
      fill: #79819A;
    }
  }
}

.xp-company-and-position {
  display: flex;
  gap: 1rem;

  &__info {
    display: flex;
    flex-direction: column;
  }
}

.xp-company-image {
  border-radius: 1rem;
  box-shadow: 0 2px 6px 0 rgba(0,0,0,0.12);
}

.xp-company, .xp-position {
  font-size: 1.125rem;
}

.xp-company {
  color: #2E2E48;
}

.xp-position {
  color: #79819A;
}

.xp-description {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  flex: 1 1 300px;

  p {
    color: #47516B;
  }

  ul {
    display: flex;
    gap: 0.5rem;
    list-style-type: none;
    flex-wrap: wrap;
  }
}
</style>