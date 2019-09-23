<template>
  <v-container>
    <v-layout text-center wrap>
      <v-form v-model="valid">
        <v-container>
          <v-row>
            <v-col cols="12" md="4">
              <v-text-field v-model="name" label="Name" required></v-text-field>
            </v-col>

            <v-col cols="12" md="4">
              <v-text-field v-model="description" label="Description" required></v-text-field>
            </v-col>
          </v-row>
          <v-btn @click="addElement">Ajouter</v-btn>
          <v-btn @click="login">Connexion</v-btn>
        </v-container>
      </v-form>
      <v-card class="mx-auto" max-width="400" tile>
        <v-list-item v-for="(item, index) in todos" v-bind:key="item.id">
          <v-list-item-content>
            <v-list-item-title>
              {{ item.name }}
            </v-list-item-title>
            <v-list-item-subtitle>
              {{ item.description }}
              <v-btn @click="rmElement(index)">Remove</v-btn>
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-card>
    </v-layout>
  </v-container>
</template>

<script>

export default {
  data: () => ({
    valid: false,
    name: '',
    description: '',
    todos: []
  }),
  methods: {
    login () {
      // connecter l'utilisateur
      this.axios.post('http://localhost:4000/api/login', {
        data: {
          login: 'louis',
          password: 'truc'
        }
      })
        .then(jsondata => console.log('response is:', jsondata))
    },
    logout () {
    },
    addElement () {
      this.todos.push({
        id: this.todos.length,
        name: this.name,
        description: this.description
      })
      console.log('ajouté !')
    },
    rmElement (index) {
      console.log('index', index)
      this.todos.splice(index, 1)
    }
  }
}
</script>
