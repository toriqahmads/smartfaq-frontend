<template>
  <div>a</div>
</template>

<script>
export default {
  middleware: ['is-auth', 'is-refresh'],
  mounted () {
    this.setPageTitle()
  },
  methods: {
    setPageTitle () {
      this.$store.commit('page-title/setAll', {
        title: 'Dashboard',
        breadcrumb: [
          {
            text: 'Dashboard',
            active: true
          }
        ]
      })
    }
  }
}
</script>
