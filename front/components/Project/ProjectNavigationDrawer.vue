<template>
  <v-navigation-drawer
    app
    clipped
    :mobile-breakpoint="mobileBreakpoint"
  >
    <v-list>
      <v-divider />

      <v-list-item
        href="https://blog.cloud-acct.com/categories/udemy"
        target="_blank"
      >
        <v-list-item-icon>
          <v-icon>
            mdi-open-in-new
          </v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>
            このアプリの作り方
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
      mobileBreakpoint: 960
    }
  }
}
</script>
