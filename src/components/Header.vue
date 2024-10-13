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
            errorInput: '',
        }
    },
    methods: {
        validation() {
            if (this.valueInput.length < 3 ) {
                this.errorInput = 'The input must be at least 3 characters';
            } else {
                this.store.repositories = {};
                this.store.users = {};
                this.errorInput = '';
                this.startLoader();
                this.getRepos(this.githubApi, this.selectedEndpoint, this.valueInput);
            }
        },
        startLoader() {
            this.store.loader = 'active';
        },
        endLoader() {
            this.store.loader = 'inactive'
        },
        getRepos(api, endpoint, name) {
            axios.get(api + endpoint, {
                params: {
                    q: name,
                    per_page: 30,
                }
            })
                .then((response) => {
                    this.store.selection = endpoint;

                    if (endpoint === 'users' && response.data.items.length > 0) {
                        this.store.users = response.data.items;
                        this.endLoader();
                        console.log(this.store.users);
                    } else if (endpoint === 'users' && response.data.items.length === 0) {
                        this.store.message = 'The user does not existe';
                        this.endLoader();
                        console.log(this.store.users);
                    } else if (endpoint === 'repositories' && response.data.items.length > 0){
                        this.store.repositories = response.data.items;
                        this.endLoader();
                        console.log(this.store.repositories);
                    } else if (endpoint === 'repositories' && response.data.items.length === 0) {
                        this.store.message = 'The repository des not existe';
                        this.endLoader();
                        console.log(this.store.repositories);
                    }
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
                <form class="d-flex col-12" role="search" @submit.prevent="validation()" >
                    <input class="form-control me-4" type="search" placeholder="Search" aria-label="Search" id="search" v-model="valueInput">
                    <select class="form-select me-4" aria-label="Default select example" v-model="selectedEndpoint">
                        <option value="users" selected >User</option>
                        <option value="repositories">Repository</option>
                    </select>
                    <button class="btn btn-outline-success">Search</button>
                </form>
            </div>
        </div>
        <span>
            {{ errorInput }}
        </span>
    </nav>

</template>

<style lang="scss" scoped>

</style>