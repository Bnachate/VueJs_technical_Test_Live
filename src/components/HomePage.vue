<template>
<v-row>
    <v-col>
    <ProfilGit
      @get-user-request="getUserGitRequest"
      :results="results"
      :error="error"
    />
    </v-col>
    <v-col>
    <ListRepo :depots="depots" />
    </v-col>
</v-row>
</template>

<script>
import axios from 'axios'

import ProfilGit from './ProfilGit.vue'
import ListRepo from './ListRepo.vue'

export default {
    components: {
        ProfilGit,
        ListRepo,
    },
    data() {
        return {
            results: [],
            depots: [],
            error: false,
        };
    },
    methods: {
        getUserRepo(user){
            axios.get(`https://api.github.com/users/${user}/repos`)
            .then((res) => {
                console.log('response', res);
                this.depots = res.data;
            })
        },
        getUserGitRequest(name) {
            axios.get(`https://api.github.com/users/${name}`)
            .then((res) => {
                // console.log('res', res);
                this.results = res.data;
                console.log('this.results', this.results);
                this.getUserRepo(name);
            })
            .catch((err) => {
                console.log('err', err);
                this.error = true;
            })
        },
    }
}
</script>