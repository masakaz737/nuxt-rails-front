<template>
  <v-navigation-drawer
    v-model="setDrawer"
    app
    clipped
    mobile-breakpoint="960"
  >
    <v-list>
      <v-divider />

      <v-list-item
        v-for="(nav, i) in navMenus"
        :key="`nav-${i}`"
        :to="$my.projectLinkTo($route.params.id, nav.name)"
      >
        <v-list-item-icon>
          <v-icon v-text="nav.icon" />
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>
            {{ $my.pageTitle(nav.name) }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
  export default {
    data () {
      return {
        navMenus: [
          { name: 'project-id-dashboard', icon: 'mdi-view-dashboard' },
          { name: 'project-id-layouts', icon: 'mdi-view-compact' },
          { name: 'project-id-pages', icon: 'mdi-image' },
          { name: 'project-id-components', icon: 'mdi-view-comfy' },
          { name: 'project-id-settings', icon: 'mdi-cog' },
          { name: 'project-id-help', icon: 'mdi-help-circle' }
        ]
      }
    },
    props: {
      drawer: {
        type: Boolean,
        default: null
      }
    },
    computed: {
      setDrawer: {
        get () { return this.drawer },
        set (val) { return this.$emit('update:drawer', val) }
      }
    }
  }
</script>
