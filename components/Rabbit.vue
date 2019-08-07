<template>
    <div>
        <div class="text-center">
            <v-avatar min-height='300px'>
                <v-img v-bind:src="profile_img" alt="avatar"
                    lazy-src="https://picsum.photos/id/11/10/6"
                    aspect-ratio="1"
                    min-width="250"
                    min-height="250">
                </v-img>
            </v-avatar>
        </div>
        <v-layout>
            <v-flex md12 xs12 sm6>
                <v-card>
                    <v-container grid-list-sm fluid>
                        <v-layout wrap>
                            <v-flex
                                v-for="item in edge_owner_to_timeline_media.edges"
                                :key="item.id"
                                xs4
                                d-flex
                                child-flex
                            >
                                <v-card flat tile class="d-flex">
                                    <v-img
                                        v-bind:src="item.node.display_url"
                                        v-bind:alt="item.node.accessibility_caption"
                                        :lazy-src="'https://picsum.photos/id/11/10/6'"
                                        aspect-ratio="1"
                                        class="grey lighten-2"
                                        >
                                        <template v-slot:placeholder>
                                            <v-layout
                                                fill-height
                                                align-center
                                                justify-center
                                                ma-0
                                            >
                                                <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                                            </v-layout>
                                        </template>
                                    </v-img>
                                </v-card>
                            </v-flex>
                        </v-layout>
                    </v-container>
                </v-card>
            </v-flex>
        </v-layout>

        <!-- <div id="id-btn">
            <button @click="getRabbit">Test btn</button>
        </div> -->
    </div>
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
    props: ["username"],
    name: 'Rabbit',
    components: {
    },
    data: () => ({
        profile_img: '',
        edge_owner_to_timeline_media: {},
    }),
    methods: {
        getRabbit() {
            http.get(`/${this.username}?__a=1`).then((response) => {
                let user = response.data.graphql.user
                this.profile_img = user.profile_pic_url_hd
                this.edge_owner_to_timeline_media.count = user.edge_owner_to_timeline_media.count
                this.edge_owner_to_timeline_media.edges = user.edge_owner_to_timeline_media.edges
                console.log(this.edge_owner_to_timeline_media.edges[0].node)
            })
           
        }
    },
    mounted() {
        this.getRabbit();
    },
}
</script>


