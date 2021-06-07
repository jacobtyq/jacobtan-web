<template>
  <div class="hero">
    <img class="hero__avatar" alt="Image of Jacob.. apparently" src="assets/profile.jpg" />
    <div class="hero__body">
      <h2>Hi, I'm Jacob 👋</h2>
      <p>I am a Software Engineer based in Singapore working on user-facing software and scalable systems.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero',
  props: {
    title: {
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
  },
  computed: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.hero {
  background: #ffffff;
  box-shadow: 0 0 50px 5px rgba(201, 201, 201, 0.25);
  padding: 16px;
  border-radius: 12px;
  display: flex;
  justify-content: center;
  align-items: center;

  &__avatar {
    border-radius: 50%;
    object-fit: cover;
    border: 1px solid #e1e4e8;
    width: 130px;
    height: 130px;
    background-color: #ffffff;
  }

  &__body {
    padding: 1rem;
  }
}
</style>
