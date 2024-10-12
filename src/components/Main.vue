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
                <img :src="repository.owner.avatar_url" class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title"> {{ repository.name }} </h5>
                    <h6 class="card-title"><em> {{ repository.full_name }} </em></h6>
                    <span class="badge text-bg-success"> {{ repository.language }} </span>
                    <p><em> {{ repository.created_at }} </em></p>
                    <p>Visibility:<em> {{ repository.visibility }} </em></p>
                    <a :href="repository.html_url" class="btn btn-primary" target="_blank" rel="noopener noreferrer" >Go to repository</a>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>