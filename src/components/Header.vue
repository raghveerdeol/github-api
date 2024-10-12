<script>
import { store }  from '../store';
import axios from 'axios';

export default {
    data() {
        return {
            githubApi: 'https://api.github.com/search/',
            store,
            selectedEndpoint: '',
            valueInput: '',
        }
    },
    methods: {
        getRepos(api, endpoint, name) {
            axios.get(api + endpoint, {
                params: {
                    q: name,
                    per_page: 30,
                }
            })
                .then((response) => {
                    this.store.repositories = response.data.items;
                    this.store.selection = endpoint;
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
            <div class="row">
                <form class="d-flex col-12" role="search" @submit.prevent="getRepos(this.githubApi, this.selectedEndpoint, this.valueInput)" >
                    <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" id="search" v-model="valueInput">
                    <select class="form-select" aria-label="Default select example" v-model="selectedEndpoint">
                        <option value="users" selected >User</option>
                        <option value="repositories">Repository</option>
                    </select>
                    <button class="btn btn-outline-success">Search</button>
                </form>
            </div>
        </div>
    </nav>

</template>

<style lang="scss" scoped>

</style>