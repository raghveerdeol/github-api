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
    <div :class=" store.loader === 'active' ? 'active' : 'inactive' ">
        <div class="loader"></div>
    </div>

    <div class="container-fluid">
        <div class="row mt-4" v-if="store.selection === 'repositories'">
            <div class="card col-3 p-3 m-2" style="width: 18rem;"  v-for="repository in store.repositories">
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

        <div class="row mt-4" v-if="store.selection === 'users'">
            <div class="card col-3 p-3 m-2" style="width: 18rem;"  v-for="user in store.users">
                <img :src="user.avatar_url" class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title"> {{ user.login }} </h5>
                    <h6 class="card-title">Id: <em> {{ user.id }} </em></h6>
                    <a :href="user.html_url" class="btn btn-primary" target="_blank" rel="noopener noreferrer" >Go to user</a>
                </div>
            </div>
        </div>

        <div class="row">
            <div class="col-10">
                {{ store.message }}
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.active{
    background-color: white;
    width: 100vw;
    height: 100vh;
}
.inactive{
    display:none
}
/* HTML: <div class="loader"></div> */
.loader {
    font-weight: bold;
    font-family: monospace;
    display: inline-grid;
    font-size: 30px;
    position: absolute;
    top: 50%;
    left: 50%;
    translate: -50% -50%;
}
.loader:before,
.loader:after {
    content:"Loading...";
    grid-area: 1/1;
    -webkit-mask-size: 100% 5px,100% 100%;
    -webkit-mask-repeat: no-repeat;
    -webkit-mask-composite: xor;
            mask-composite: exclude;
    animation: l35-1 1s infinite;
}
.loader:before {
    -webkit-mask-image:
    linear-gradient(#000 0 0),
    linear-gradient(#000 0 0);
}
.loader:after {
    -webkit-mask-image:
        linear-gradient(#000 0 0);
    animation:
        l35-1  1s infinite,
        l35-2 .2s infinite cubic-bezier(0.5,200,0.5,-200);
}

@keyframes l35-1{
    0%   {-webkit-mask-position:0 20px,0 0}
    20%  {-webkit-mask-position:0 8px ,0 0}
    40%  {-webkit-mask-position:0 100%,0 0}
    60%  {-webkit-mask-position:0 3px ,0 0}
    80%  {-webkit-mask-position:0 15px,0 0}
    100% {-webkit-mask-position:0 0   ,0 0}
}
@keyframes l35-2{
    100% {transform:translate(0.1px)} 
}
</style>