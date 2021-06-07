<template>
  <div class="header">
    <nav>
      <div class="navigation">
        <div class="logo">
          <a>Jacob Tan</a>
        </div>
        <div class="navigation--links">
          <router-link to="/">Home</router-link>
          <!-- <router-link to="/about">About</router-link> -->
          <a
            :href="blogUrl"
            target="_blank"
            rel="noreferrer"
            aria-label="Link to Jacob's Blog"
            >Blog</a
          >
          <a
            :href="gitHub"
            target="_blank"
            rel="noreferrer"
            aria-label="Link to Jacob's GitHub"
            >GitHub</a
          >
          <a
            :href="linkedIn"
            target="_blank"
            rel="noreferrer"
            aria-label="Link to Jacob's LinkedIn"
            >LinkedIn</a
          >
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      blogUrl: 'https://blog.jacobtan.co/',
      gitHub: 'https://github.com/jacobtyq',
      linkedIn: 'https://www.linkedin.com/in/jacob-tan-60b0b963/'
    }
  },
  components: {}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.navigation {
  $navigation-width: 960px;

  display: grid;
  grid-template-columns: 50% 50%;
  height: 60px;
  align-content: center;
  max-width: $navigation-width;
  margin: 0 auto;

  @media (max-width: $navigation-width) {
    padding: 1rem;
  }

  @media (max-width: 767px) {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .logo {
    text-align: left;

    a {
      font-size: 1.2rem;
      font-weight: bold;
      color: #1a535c;
    }
  }

  &--links {
    text-align: right;

    @media (max-width: 767px) {
      position: fixed;
      z-index: 9999;
      right: 0;
      bottom: 0;
      left: 0;
      background: #ffffff;
      box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.25);
      display: flex;
      align-items: center;
      justify-content: center;
      height: 60px;
    }

    a {
      text-decoration: none;
      color: #1a535c;
      font-size: 1rem;
      font-weight: bold;
      margin: 0 8px;

      @media (max-width: 767px) {
        margin: 0 30px;
      }

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
