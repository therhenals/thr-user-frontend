<template>
  <div class="HomePage">
    <v-app-bar flat color="rgba(0, 0, 0, 0)">
      <v-btn to="/" icon>
        <v-icon>mdi-arrow-left</v-icon>
      </v-btn>
      <v-spacer />
      <v-toolbar-title class="title white--text pl-0">
        Usuario: {{ $route.params.id }}
      </v-toolbar-title>
    </v-app-bar>
    <v-row>
      <v-col v-for="post in posts" :key="post.id" cols="12" sm="4">
        <v-card>
          <v-card-title>
            {{ post.title }}
          </v-card-title>
          <v-card-text>
            {{ post.body }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  head: {
    title: 'Posts',
  },
})
export default class HomePage extends Vue {
  async asyncData({ $axios, params }: any) {
    const posts = await $axios.$get(`/api/posts/${params.id}`)
    return { posts }
  }
}
</script>
