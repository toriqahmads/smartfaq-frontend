<template>
  <div class="sidebar">
    <template v-for="(list, li) in lists">
      <div :key="li" class="sidebar-lists">
        <div class="sidebar-lists-title">
          {{ list.name }}
        </div>
        <div class="sidebar-menus">
          <template v-for="(menu, mi) in list.menus">
            <b-link
              :key="mi"
              class="sidebar-menus-link"
              :to="menu.to"
              @click="clickLink"
            >
              <fa-layers class="fa-fw">
                <fa-icon :icon="menu.icon" />
              </fa-layers>
              {{ menu.name }}
            </b-link>
          </template>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    toggle: {
      type: Boolean,
      require: false
    }
  },
  computed: {
    lists () {
      return this.$tools.lists
    }
  },
  methods: {
    clickLink () {
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
