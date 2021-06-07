<template>
  <div class="cards">
    <app-card v-for="project in projects" 
        :key="project.id" 
        v-bind:title="project.title"
        v-bind:tag="project.tag"
        v-bind:textColor="project.textColor"
        v-bind:className="project.className"
        v-bind:url="project.url"
    /> 
  </div>
</template>

<script>
import Card from '@/components/Card'

export default {
  name: 'Header',
  data () {
    return {
        projects: [
            {
                title: "Spacemob",
                tag: "Development",
                textColor: "#31B28D",
                className: "spacemob",
                url: "https://www.spacemob.co/"
            },
            {
                title: "Giving",
                tag: "Development",
                textColor: "#7955B4",
                className: "giving",
                url: "https://www.giving.sg/"
            },
            {
                title: "Mrt-tan",
                tag: "Development, Design",
                textColor: "rgb(188, 100, 27)",
                className: "mrttan",
                url: "https://mrt-tan.com"
            },
            {
                title: "Watchcrypto",
                tag: "Development, Design",
                textColor: "#23d260",
                className: "watchcrypto",
                url: "https://watchcrypto.today"
            },
            {
                title: "Innocellence",
                tag: "Development",
                textColor: "#EF4B46",
                className: "innocellence",
                url: "http://www.innocellence.com/"
            }
        ]
      }
  },
  components: {
    'app-card': Card
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.cards {
  $max-width: 960px;

  width: 100%;
  max-width: $max-width;
  display: flex;

  @media (max-width: $max-width) {
    flex-flow: row wrap;
  }
}
</style>
