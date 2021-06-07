<template>
    <div>
        <section class="body">
            <app-hero></app-hero>
            <h4 class="header-title">Latest Posts</h4>
            <app-post></app-post>
            <h4 class="header-title">Past Projects</h4>
            <app-cards></app-cards>
        </section>
    </div>
</template>

<script>
import Hero from '@/sections/Hero'
import Cards from '@/sections/Cards'
import Post from '@/components/Post'

export default {
  name: 'Body',
  data () {
    return {}
  },
  components: {
    'app-cards': Cards,
    'app-post': Post,
    'app-hero': Hero
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.body {
    $max-width: 960px;

    max-width: $max-width;
    margin: 50px auto;

    text-align: left;

    margin-bottom: 40px;
    min-height: 100%;
    position: relative;

    @media (max-width: 767px) {
        margin: 0 auto;
        margin-bottom: 30px;
    }

    @media (max-width: 960px) {
        padding: 1rem;
    }

    .header-title {
        margin-left: 8px;
        font-size: 1.2rem;
        position: relative;
        color: #1A535C;

        &:after {
            content: "";
            position: absolute;
            z-index: -1;
            bottom: -4px;
            left: -3px;
            background: #FFE66D;
            width: 4.5rem;
            height: 6px;
        }
    }
}
</style>
