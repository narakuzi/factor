<template>
  <section id="portfolio" class="page-container portfolio-container">
    <div class="header">
      <h2 class="pretitle">{{ setting('portfolio.pretitle') }}</h2>
      <h1 class="title">{{ setting('portfolio.title') }}</h1>
    </div>
    <div class="content">
      <portfolio-index />

      <div class="clients-wrap">
        <h2 class="clients-title">{{ setting('portfolio.clientsTitle') }}</h2>
        <div class="clients">
          <div v-for="(logo, i) in setting('portfolio.clients')" :key="i" class="logo">
            <img :src="logo.picture" :alt="logo.alt" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { setting } from "@factor/api/settings"
import Vue from "vue"

export default Vue.extend({
  components: {
    "portfolio-index": () => import("./portfolio/portfolio-index.vue")
  },
  methods: { setting }
})
</script>

<style lang="less">
.portfolio-container {
  padding: 0;

  .header {
    background: var(--color-text);
    padding: 4em 4em 8em;

    @media (max-width: 900px) {
      padding: 3em 2em 5em;
    }

    .pretitle {
      color: var(--color-text-gray);
      font-size: 1.4em;
      text-align: center;
      @media (max-width: 900px) {
        font-size: 1.2rem;
      }
    }
    .title {
      font-size: 3.2em;
      font-weight: var(--font-weight-bold);
      letter-spacing: -0.03em;
      line-height: 1.1;
      color: var(--color-text-light);
      text-align: center;
      max-width: 800px;
      margin: 0 auto 1rem;
      @media (max-width: 900px) {
        font-size: 2.2rem;
      }
    }
  }

  .content {
    background: var(--color-white);
    padding: 0 4em 4em;
    @media (max-width: 900px) {
      padding: 0 2em 3em;
    }

    .posts-wrap {
      margin-top: -4em;
      .portfolio-posts {
        display: grid;
        grid-gap: 10px;
        grid-template-columns: 1fr 1fr;

        @media (max-width: 900px) {
          grid-template-columns: 1fr;
        }
      }
    }
  }

  .clients-wrap {
    text-align: center;
    margin-top: 4em;
    .clients-title {
      font-size: 2em;
      font-weight: var(--font-weight-bold);
      letter-spacing: -0.03em;
      line-height: 1.1;
      color: var(--color-text);
      margin-bottom: 2rem;
      text-align: center;
      @media (max-width: 900px) {
        font-size: 1.8rem;
      }
    }
    .clients {
      display: grid;
      grid-gap: 3em;
      grid-template-columns: 1fr 1fr 1fr 1fr;
      align-items: center;

      @media (max-width: 900px) {
        grid-template-columns: 1fr 1fr;
      }
      .logo img {
        width: 100%;
        height: auto;
      }
    }
  }
}
</style>
