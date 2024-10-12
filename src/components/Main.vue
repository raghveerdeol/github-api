<script>
import axios from 'axios';
import { store } from "../store";
export default {
    data() {
        return {
            store,
        }
    },
}
</script>

<template>
    <div class="container-fluid">
        <div class="row">
            <div class="card col-3" style="width: 18rem;"  v-for="repository in store.repositories">
                <img src="..." class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title"> {{ repository.name }} </h5>
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
                        content.</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>