<template>
<v-container bg fill-height grid-list-md text-xs-center>
        <v-layout row wrap align-center>
          <v-flex>
            <v-text-field
                v-model="profileName"
                placeholder="@Instagram"
                color="#ff7675"
                single-line
                outlined
            ></v-text-field>
            <v-btn v-on:click="this.handleClick" large color="#ff7675" style="width: 100%">Touch me, plzzz!!!</v-btn>
          </v-flex>
        </v-layout>
      </v-container>
</template>

<script>
import axios from 'axios'

axios.defaults.baseURL = 'https://instagram.com'
axios.defaults.timeout = 30000

axios.interceptors.request.use(
  config => config,
  error => Promise.reject(error)
);

axios.interceptors.response.use(
  response => response,
  error => Promise.reject(error)
);

const http = {
    get(url, config = {}) {
        return axios.get(url, config)
    }
}

export default {
    name: 'Ig-form',
    components: {
    },

    data() {
        return {
            profileName: ""
        }
    },

    methods: {
        handleClick() {
            this.$router.push({
                path: "/profile",
                query: {username: this.profileName}
            })
        }
    }
}
</script>

