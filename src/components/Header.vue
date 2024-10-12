<script>
import { store }  from '../store';
import axios from 'axios';

export default {
    data() {
        return {
            githubApi: 'https://api.github.com/search/repositories',
            store,
            valueInput: '',
        }
    },
    methods: {
        getRepos(api, name) {
            axios.get(api, {
                params: {
                    q: name,
                    per_page: 30,
                }
            })
                .then((response) => {
                    this.store.repositories = response.data.items;
                    console.log(this.store.repositories);
                })
                .catch(function (error) {
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });
        }
    },
    // created() {
    //     this.getRepos(this.githubApi, this.valueInput);
    // }
}
</script>

<template>
    <nav class="navbar bg-body-tertiary">
        <div class="container-fluid">
            <form class="d-flex" role="search" @submit.prevent="getRepos(this.githubApi, this.valueInput)" >
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" id="search" v-model="valueInput">
                <button class="btn btn-outline-success">Search</button>
            </form>
        </div>
    </nav>

</template>

<style lang="scss" scoped>

</style>