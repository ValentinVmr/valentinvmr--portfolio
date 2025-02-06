<script lang="ts" setup>
import { Analytics } from '@vercel/analytics/nuxt'

useHead({
  title: 'hoorah!',
  meta: [{ name: 'description', content: 'hoorah!' }],
  link: [{ rel: 'icon', type: 'image/png', href: '/favicon.png' }],
})

const technicalSkills = [
  "Spring Boot",
  "Java",
  "Angular 8",
  "Vue.js 3",
  "Docker",
  "Leadership",
  "Architecture hexagonale",
  "Domain Driven Design",
  "TDD/BDD",
  "Cucumber",
  "Github Actions"
]

const projects: any[] = [
  {
    name: "Sleepless Night",
    description: "Développement du site web de l'association Sleepless Night, organisateur d'évènements caritatifs sur Twitch",
    image: "/statics/sleepless-night.png",
    link: "https://sleeplessnight.fr"
  },
  {
    name: "Duel Sync",
    description: "Application permettant de suivre ses points de vie. Pratique lors de Remote Duels",
    image: "/statics/duel-sync.png",
    link: "https://duel-sync.vercel.app/",
    github: "https://github.com/ValentinVmr/valentinvmr--Duel-Sync"
  },
  {
    name: "Buzzzed",
    description: "Création de buzzers en ligne afin d'éviter les fameux \"c'est moi qui l'ai dit en premier\" !",
    image: "/statics/buzzzed.png",
    link: "https://buzzzed.sleeplessnight.fr/",
    github: "https://github.com/ValentinVmr/valentinvmr--buzzzed"
  },
  {
    name: "Portfolio",
    description: "Développement de mon portfolio personnel avec Nuxt.js",
    image: "/statics/portfolio.jpg",
    github: "https://github.com/ValentinVmr/valentinvmr--portfolio",
    link: "https://hoorah.fr"
  },
  {
    name: "Donation Goal Manager",
    description: "Mise en place du listener de dons pour l'association Sleepless Night",
    image: "/statics/dgm.jpg",
  }
]

const experiences = [
  {
    company: 'Leroy Merlin',
    position: 'Developer / Lead Developer',
    startDate: 'Juin 2019',
    description: 'En tant que <strong>Lead Developer</strong>, j\'ai <strong>encadré le développement et assuré la mise en ligne des configurateurs </strong>pour les produits Porte de Placard et Plan de Travail. J\'ai <strong>animé une équipe technique, favorisant la montée en compétences des développeurs</strong>, en <strong>apportant mon expertise pour trancher sur des choix techniques </strong>et garantir la qualité des livrables.',
    skills: ['Spring Boot', 'Java 17', 'Architecture hexagonale', 'Vue.js 3', 'Angular 8', 'Leadership', 'Egoless Programming'],
    city: 'Lezennes',
    companyImage: '/statics/companies/lm.png',
  },
  {
    company: 'Leroy Merlin',
    position: 'Developer / Lead Developer',
    startDate: 'Août 2021',
    endDate: 'Déc. 2022',
    description: 'J\'ai d\'abord continué pendant un an sur les Outils d\'Aide à la Pose (OAP), où j\'ai <strong>lead l\'équipe de développement </strong>et ait <strong>contribué à l\'évolution et à la maintenance </strong>des outils dédiés à la gestion de la pose de produits. J\'ai ensuite contribué sur un outils de suivi des prestations de pose et de livraison des produits.',
    skills: ['Spring Boot', 'Java 8', 'Angular 8', 'React.js', 'Elastic Search', 'Leadership', 'Egoless Programming'],
    city: 'Lezennes',
    companyImage: '/statics/companies/lm.png',
  },
  {
    company: 'Open',
    position: 'Lead Developer',
    startDate: 'Juin 2019',
    endDate: 'Août 2021',
    description: 'Dans ce rôle, <strong>j\'ai contribué à moderniser les outils d\'aide à la pose en participant à la création d\'une nouvelle solution innovante.</strong>En tant que <strong>référent technique</strong>, j\'ai <strong>animé l\'équipe de développement</strong> pour garantir la qualité des livrables et assurer une intégration fluide des nouvelles fonctionnalités.',
    skills: ['Spring Boot', 'Java 8', 'Angular 8', 'Leadership'],
    city: 'Lezennes',
    companyImage: '/statics/companies/open.jpg',
  }
]
</script>

<template>
  <Analytics />
  <HoorahNavigation/>
  <section class="portfolio">
    <section class="portfolio__welcome">
      <h1>Hello, bienvenue chez</h1>
      <HoorahLogo class="portfolio__welcome__logo"/>
      <h1>Ensemble, donnons vie à vos projets 🌟</h1>
    </section>
    <section class="portfolio__header">
      <div class="portfolio__header__information">
        <HoorahAvatar avatar="/statics/avatar.jpeg" width="150" height="150"/>
        <div class="portfolio__header__information__text" id="about">
          <h1 class="portfolio__header__information__text__name">Valentin Vamour</h1>
          <p class="portfolio__header__information__text__description">Lead Developer</p>
          <p class="portfolio__header__information__text__about-me">
            <strong>Lead Developer Full Stack</strong> avec une <strong>forte expérience dans la gestion de projets
            complexes</strong>
            et avec <strong>un tas de side projects toujours en cours</strong>, j'aime <strong>accompagner mon équipe
            dans
            sa montée en puissance</strong> et <strong>l'emmène avec moi vers un objectif commun, fort de sens</strong>
            pour mon client et ses utilisateurs finaux.
          </p>
        </div>

      </div>
    </section>
    <main class="portfolio__main">
      <section class="portfolio__skills">
        <h2 id="skills">Compétences</h2>
        <ul class="portfolio__skills__list">
          <li v-for="skill in technicalSkills">
            <HoorahSkill :skill="skill"/>
          </li>
        </ul>
      </section>
      <section class="portfolio__projects">
        <h2 id="projects">Projets</h2>
        <ul class="portfolio__projects__list">
          <li v-for="project in projects">
            <HoorahProject :name="project.name"
                           :description="project.description"
                           :image="project.image"
                           :link="project.link"
                           :in-progress="project.inProgress"
                           :github="project.github"
                           :background-color="project.backgroundColor"
            />
          </li>
        </ul>
      </section>
      <section class="portfolio__xp">
        <h2 id="experiences">Expériences</h2>
        <ul class="portfolio__xp__list">
          <li v-for="xp in experiences">
            <div class="portfolio__xp__list__thread">
              <span class="icon">•</span>
              <span class="thread"></span>
            </div>
            <HoorahExperience :company="xp.company"
                              :position="xp.position"
                              :startDate="xp.startDate"
                              :endDate="xp.endDate"
                              :description="xp.description"
                              :skills="xp.skills"
                              :city="xp.city"
                              :companyImage="xp.companyImage"
            />
          </li>
        </ul>
      </section>
      <section class="portfolio__contact">
        <h2 id="contact">Intéressé(e) par mon profil ?</h2>
        <article class="portfolio__contact__availability">
          <p>Je suis actuellement <HoorahAvailability :availability="false" /></p>
        </article>
        <article>
          <div>
            <h3>Retrouvez-moi ici 👇</h3>
            <ul>
              <li>
                <a href=""><IconLinkedIn />LinkedIn</a>
              </li>
              <li>
                <a href="https://github.com/ValentinVmr"><IconGithub />Github</a>
              </li>
              <li>
                <a href="mailto:valentin.vamour@hoorah.fr"><IconMail />E-mail</a>
              </li>
            </ul>
          </div>
          <a class="download-resume" href="https://drive.google.com/file/d/1sv1F7QfiuWUfaiNpS4YxZhi2qDWU3-5d/view?usp=sharing">
            <IconDownload />Télécharger mon CV
          </a>
        </article>
      </section>
    </main>
    <footer>
      Copyright © 2025 Valentin Vamour
    </footer>
  </section>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@100..900&display=swap');
[id] {
  scroll-margin-top: 100px;
}

html {
  scroll-behavior: smooth;
}

* {
  box-sizing: border-box;
  font-family: 'Outfit', sans-serif;
  margin: 0;
  padding: 0;
  color: #121417;
}

a:hover {
  color: #171c1e;
}

h2 {
  margin-bottom: 1.5rem;
  font-size: 2.25rem;
}

h3 {
  margin-bottom: 0.5rem;
}

footer {
  text-align: center;
  padding: 1rem;
  margin-top: 3rem;
}

.portfolio {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 3rem;
  padding: 0.5rem 1rem 6rem;

  &__welcome {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    align-items: center;
    padding: 1rem;
    margin-bottom: 3rem;
    text-align: center;
    background: url("/statics/welcome.svg") center center;
    border: 1px solid rgba(99, 117, 135, 0.125);
    border-radius: 8px;
    position: relative;

    &__logo {
      max-width: 600px;
    }
  }

  @media screen and (min-width: 680px) {
    padding: 2rem 4rem;
  }

  &__main {
    display: flex;
    flex-direction: column;
    gap: 5rem;
  }

  &__header {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    background: #ECF3F4;
    padding: 1.5rem;
    border-radius: 8px;

    &__information {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      flex: 1;

      & .avatar {
        flex: 33.3333%;
      }

      &__text {
        flex: 66.6666%;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;

        &__name {
          font-size: 1.375rem;
          text-wrap: nowrap;
        }

        &__description {
          color: #637587;
          text-wrap: nowrap;
        }

        &__about-me {
          font-size: 1rem;
          text-wrap: normal;
        }
      }
    }

    &__links {
      align-self: end;

      ul {
        display: flex;
        gap: 0.25rem;
        list-style-type: none;
        justify-content: flex-end;
        border-top: 1px solid #d5dbdc;
        padding: 1rem 0;

        @media screen and (min-width: 680px) {
          padding: 0;
          flex-direction: column;
          border-top: none;
          width: 100%;
        }

        a {
          font-size: 1rem;
          text-decoration: none;
          display: flex;
          gap: 0.5rem;
          align-items: center;
        }

        svg {
          width: 24px;
          height: 24px;
        }
      }
    }
  }

  &__skills {
    &__list {
      display: flex;
      gap: 1rem;
      list-style-type: none;
      flex-wrap: wrap;
    }
  }

  &__projects {
    &__list {
      display: grid;
      gap: 2rem 1rem;
      grid-template-columns: repeat(auto-fit, minmax(calc(1280px / 5), 1fr));
      list-style-type: none;

      li {
        align-self: stretch;
      }
    }
  }

  &__xp {
    &__list {
      display: flex;
      flex-direction: column;
      gap: 3rem;
      list-style-type: none;

      li {
        display: flex;

        @media screen and (min-width: 680px) {
          gap: 1.5rem;
        }

        &:last-child {
          .thread {
            display: none;
          }
        }
      }

      &__thread {
        display: flex;
        gap: 1rem;
        position: relative;

        .icon {
          display: none;
        }

        .thread {
          display: none;
        }

        @media screen and (min-width: 680px) {
          .icon {
            display: flex;
            background: white;
            box-shadow: 0 2px 6px 0 rgba(0,0,0,0.12);
            border-radius: 50%;
            width: 2rem;
            height: 2rem;
            font-size: 2rem;
            justify-content: center;
            align-items: center;
            z-index: 3;
          }

          .thread {
            display: block;
            flex: 1;
            width: 2px;
            height: calc(100% + 4rem);
            top: 2px;
            left: calc(50% - 1px);
            background: #E2E6EE;
            position: absolute;
            z-index: 2;
          }
        }
      }
    }
  }

  &__contact {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    padding: 1.5rem;
    border-radius: 8px;

    &__availability {
      p {
        display: flex;
        flex-direction: column;
        gap: 0.25rem;
        align-items: center;
        justify-content: center;
      }
    }

    h2 {
      margin: 0;
      font-size: 1.5rem;
    }

    background: #ECF3F4 url("/statics/welcome.svg") center center;

    .download-resume {
      display: flex;
      gap: 0.5rem;
      align-items: center;
      justify-content: center;
      padding: 1rem;

      background: #2e3233;
      color: white;
      border-radius: 4px;

      svg {
        width: 1.5rem;
        height: 1.5rem;
        fill: white;
      }
    }

    h2, h3 {
      text-align: center;
    }

    & > article {
      display: flex;
      flex-direction: column;
      gap: 2rem;
      align-items: center;
    }

    ul {
      display: flex;
      gap: 1rem;
      justify-content: center;
      list-style-type: none;
      flex-wrap: wrap;

      li {

        a {
          display: flex;
          gap: 0.5rem;
          align-items: center;
        }

        svg {
          width: 2rem;
          height: 2rem;
        }
      }
    }
  }
}
</style>