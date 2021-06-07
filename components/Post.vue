<template>
  <div class="posts">
    <div class="post" :key="index" v-for="(post, index) in posts.slice(0, 3)">
      <a :href="post.url" target="_blank" rel="noopener noreferrer" v-bind:aria-label="post.title">
        <img :src="post.feature_image" v-if="post.feature_image" alt="" />
        <div class="post__header">
          <p class="post__header-title">{{ post.title }}</p>
          <p class="post__stats">
            {{ post.published_at | moment("ddd, MMM Do YYYY") }} /
            <app-readingTime v-bind:time="post.reading_time" />
          </p>
        </div>
        <div class="post__summary">
          <p>{{ post.excerpt }}</p>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
import ReadingTime from '@/components/ReadingTime'

export default {
  name: 'Post',
  components: {
    'app-readingTime': ReadingTime
  },
  data: function () {
    return {
      posts: [],
      status: ''
    }
  },
  props: {
    lines: {
      default: 4
    },
    skeletons: {
      default: 3
    }
  },
  methods: {
    async getPosts () {
      await this.$axios
        .$get(
          this.$config.GHOST_BLOG_URI + 'ghost/api/v3/content/posts/?key=' + this.$config.GHOST_API_KEY
        )
        .then(res => {
          this.posts = res.data.posts
          this.loadSkeletons = false
        })
        .catch(err => {
          console.error(err)
        })
    },
    getReadingTime (time) {
      return Math.round(time)
    }
  },
  created: function () {
    this.getPosts()
  },
  filters: {
    formatUnix: function (value) {
      if (value) {
        const readableDate = new Date(value * 1)
        const locale = 'en-sg'
        return (
          readableDate.getDate() +
          ' ' +
          readableDate.toLocaleString(locale, { month: 'long' }) +
          ' ' +
          readableDate.getFullYear()
        )
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.posts {
  $max-width: 960px;

  max-width: $max-width;
  width: 100%;

  display: grid;
  grid-gap: 12px;
  grid-template-columns: repeat(auto-fill, minmax(282px, 1fr));
  grid-auto-rows: 500px;
  @media (max-width: $max-width) {
    flex-flow: row wrap;
  }
}

.post {
  $max-width: 960px;
  $header-black: #141726;
  border-radius: 6px;

  background: #ffffff;
  color: #b5b5b5;
  position: relative;
  box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.25);
  transition: all 0.3s ease;
  cursor: pointer;

  overflow: hidden;

  &:hover {
    box-shadow: 6px 6px 50px 2px rgba(201, 201, 201, 0.6);
    z-index: 2;
    cursor: pointer;
  }

  img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  &__header {
    &-title {
      font-size: 1.125rem;
      font-weight: bold;
      margin: 0;
      color: #1a535c;
      font-family: "Open Sans", sans-serif;
      margin-top: 20px;
    }

    &-tag {
      font-weight: bold;
      text-transform: uppercase;
      font-size: 0.8rem;
    }
  }

  &__summary {
    color: #051011;
    line-height: 1.5;
    // font-family: 'Crimson Text', serif;
    font-family: "Avenir", Helvetica, Arial, sans-serif;

    &-tag {
      font-weight: bold;
      text-transform: uppercase;
      font-size: 0.8rem;
      margin: 0;
      padding: 0;
    }

    p {
      // max-height: 4rem;
      position: relative;
      display: -webkit-box;
      -webkit-line-clamp: 5;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    @supports not (display: -webkit-box) {
      p {
          &:after {
            content: "";
            text-align: right;
            position: absolute;
            bottom: 0;
            right: 0;
            width: 70%;
            height: 1.2em;
            background: linear-gradient(
              to right,
              rgba(255, 255, 255, 0),
              rgba(255, 255, 255, 1) 50%
            );
          }
      }
    }
  }

  &__header,
  &__summary {
    padding: 0 25px;
  }

  &__stats {
    color: #1a535c;
    font-size: 0.9rem;
    font-weight: bold;
  }

  a {
    text-decoration: none;
  }

  &__skeleton {
    width: calc(100% - (16px * 3));
    height: auto;
    margin: 0 8px;

    padding: 16px;
    border-radius: 12px;

    background: #ffffff;
    color: #b5b5b5;
    position: relative;
    box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.25);

    @keyframes load {
      0% {
        background: rgb(249, 249, 249);
      }

      25% {
        background: rgb(237, 237, 237);
      }

      50% {
        background: rgb(223, 223, 223);
      }

      75% {
        background: rgb(237, 237, 237);
      }

      100% {
        background: rgb(249, 249, 249);
      }
    }

    &-header {
      width: 100%;
      height: 1.3rem;
      background-color: rgba(133, 133, 133, 0.25);
      animation: load 2s;
    }

    &-summary {
      margin-top: 46px;

      &--text {
        width: 100%;
        background-color: rgba(201, 201, 201, 0.25);
        height: 1.1rem;
        line-height: 1.5;
        margin: 12px 0;
        animation: load 2s;
      }
    }

    &-stats {
      width: 40%;
      height: 1.1rem;
      background-color: rgba(166, 166, 166, 0.25);
      margin-top: 50px;
      animation: load 2s;
    }
  }
}
</style>
