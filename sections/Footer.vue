<template>
  <div>
    <footer>
      <div class="footer">
        <p>
          &copy;jacobtan.co&nbsp;2019-{{ currentYear() }}
        </p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Footer',
  data: function() {
    return {}
  },
  methods: {
    currentYear: () => {
      return new Date().getFullYear()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
.footer {
  height: 40px;
  width: 100%;

  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;
  bottom: 0;

  p {
    font-size: 0.9rem;
    text-align: center;
    font-weight: bold;

    a {
      color: #1a535c;
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
