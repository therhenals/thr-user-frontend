<template>
  <div class="HomePage">
    <v-row>
      <v-col v-for="user in users" :key="user.id" cols="12" sm="4">
        <v-card>
          <v-card-title>
            {{ user.name }}
          </v-card-title>
          <v-card-text>
            <v-list two-line>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>Email</v-list-item-title>
                  <v-list-item-subtitle>{{ user.email }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>

              <v-divider></v-divider>

              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>Username</v-list-item-title>
                  <v-list-item-subtitle>{{
                    user.username
                  }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>

              <v-divider></v-divider>
            </v-list>
          </v-card-text>
          <v-card-actions>
            <v-btn color="teal accent-4" :to="`/${user.id}`">
              Posts
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  head: {
    title: 'Inicio',
  },
})
export default class HomePage extends Vue {
  async asyncData({ $axios }: any) {
    const users = await $axios.$get('/api/users')
    return { users }
  }
}
</script>
