<template>
  <b-navbar type="dark" variant="dark" fixed="top" class="header">
    <b-navbar-brand to="/" @click="clickBrandMobile">
      Smart FAQ
    </b-navbar-brand>
    <b-button class="header-bars order-1 order-lg-0" size="sm" variant="link" @click="clickBars">
      <fa-layers class="fa-fw">
        <fa-icon :icon="['fas', 'bars']" />
      </fa-layers>
    </b-button>
    <b-navbar-nav class="ml-auto">
      <b-nav-item-dropdown right>
        <template #button-content>
          <fa-layers class="fa-fw">
            <fa-icon :icon="['fas', 'user']" />
          </fa-layers>
        </template>
        <b-dropdown-item to="/setting">
          Setting
        </b-dropdown-item>
        <b-dropdown-divider />
        <b-dropdown-item>
          Logout
        </b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>
  </b-navbar>
</template>
<script>
export default {
  props: {
    toggle: {
      type: Boolean,
      require: false
    }
  },
  methods: {
    clickBars () {
      this.$emit('toggle-sidebar', !this.toggle)
    },
    clickBrandMobile () {
      const winWidth = $(window).width()
      if (winWidth <= 767) {
        if (this.toggle) {
          this.$emit('toggle-sidebar', false)
        }
      }
    }
  }
}
</script>
