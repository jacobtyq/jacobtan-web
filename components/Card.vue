<template>
  <div class="card" :class="className">
    <a :href="url" target="_blank" rel="noopener noreferrer">
      <div class="card__header" :style="{ color: textColor }">
        <div class="card__header-tag">{{ tag }}</div>
        <div class="card__header-title">{{ title }}</div>
      </div>
      <div class="card__image">
        <img :src="'/static/' + className + '.png'" :alt="className" />
      </div>
    </a>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: {
      type: String,
      default: 'Project Name'
    },
    tag: {
      type: String,
      default: 'Web Development'
    },
    url: {
      type: String,
      default: '/'
    },
    textColor: {
      type: String,
      default: '#B5B5B5'
    },
    backgroundColor: {
      type: String,
      default: '#FFFFFF'
    },
    className: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      hoverState: false,
      card: {
        backgroundColor: '#FFFFFF'
      }
    }
  },
  methods: {
    updateHoverState (isHover) {
      this.hoverState = isHover
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.card {
  $max-width: 960px;

  width: calc(100% - (16px * 3));
  height: 300px;
  margin: 0 8px;

  padding: 16px;
  border-radius: 12px;

  background: #ffffff;
  color: #b5b5b5;
  position: relative;
  box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.25);
  transition: all 0.3s ease;
  cursor: pointer;

  overflow: hidden;

  @media (max-width: $max-width) {
    width: calc(50% - (16px * 3));
    margin: 8px;
  }

  a {
    text-decoration: none;

    &:hover {
      color: #fff;
    }
  }

  &:hover {
    transform: translateY(-10px);
    box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.4);
    color: rgb(96, 96, 96);
    background: transparent;
    border-radius: 12px;
  }

  &:before {
    position: absolute;
    content: "";
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 12px;
  }

  &.spacemob {
    &:hover {
      background: #31b28d;
      box-shadow: 0 0 50px 5px rgba(49, 178, 141, 0.4);

      .card__header {
        color: #fff !important;
      }
    }
  }

  &.giving {
    &:hover {
      background: #7955b4;
      box-shadow: 0 0 50px 5px rgba(121, 85, 180, 0.4);

      .card__header {
        color: #fff !important;
      }
    }
  }

  &.mrttan {
    &:hover {
      background: rgb(188, 100, 27);
      box-shadow: 0 0 50px 5px rgba(188, 100, 27, 0.4);

      .card__header {
        color: #fff !important;
      }
    }
  }

  &.watchcrypto {
    &:hover {
      background: #23d260;
      box-shadow: 0 0 50px 5px rgba(35, 210, 96, 0.4);

      .card__header {
        color: #fff !important;
      }
    }
  }

  &.innocellence {
    &:hover {
      background: #ef4b46;
      box-shadow: 0 0 50px 5px rgba(239, 75, 70, 0.4);

      .card__header {
        color: #fff !important;
      }
    }
  }

  &__header {
    position: relative;
    overflow: hidden;
    text-align: left;

    &-tag {
      font-weight: bold;
      text-transform: uppercase;
      font-size: 0.8rem;
    }

    &-title {
      font-size: 1.2rem;
      font-weight: bold;
    }
  }

  &__image {
    object-fit: cover;

    img {
      background-color: #ffffff;
      overflow: hidden;
      border-radius: 12px;

      transform: rotate(-20deg);
    }
  }
}
</style>
