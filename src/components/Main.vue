<script>
import axios from 'axios';

export default {
    data() {
        return {
            githubApi: 'https://api.github.com/search/repositories'
        }
    },
    methods: {
        getRepos() {
            axios.get('https://api.github.com/search/repositories', {
                params: {
                    q: 'profume',
                    per_page: 30,
                }
            })
                .then(function (response) {
                    console.log(response.data.items);
                })
                .catch(function (error) {
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });
        }
    },
    created() {
        this.getRepos();
    }

}
</script>

<template>
    <div class="card" style="width: 18rem;">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
                content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
    </div>
</template>

<style scoped></style>