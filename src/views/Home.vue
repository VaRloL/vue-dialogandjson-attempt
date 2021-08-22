<template>
    <v-container>
        <h2 class="white--text text-left">Welcome to the main page!</h2>
        <v-divider dark class="my-2"></v-divider>
        <div class="pb-2"> 
            <h3 class="white--text text-left">Top Today</h3>
            <div class="d-flex flex-row" style="overflow-x:auto;">
             <div v-for="items, index of users" :key="index" class="mx-1 pa-2 rounded d-flex flex-column" style="background:#252525; width:200px; min-width:200px">
                 <v-avatar size="100" class="align-self-center"><v-img :src="photos[index]"/></v-avatar>
                 <p class="white--text text-left text-h5 my-1">{{items.name}}</p>
                 <p class="white--text text-center">{{items.username}}</p>
                 <v-btn color="success" class="mt-auto" @click="dialogEdit(items.email, items.phone, items.website)">Contact</v-btn>
             </div>
             </div>
            <v-divider dark class="my-2"></v-divider>
            <v-dialog v-model=currentEdit.isOn class="pa-0 ma-0">
                <v-card dark class="pa-2 d-flex flex-column" outlined>
                    <v-card-title class="align-self-center text-h4 mb-2">User Info</v-card-title>
                    <v-card-subtitle class="text-h5">Email</v-card-subtitle>
                    <v-card-text class="text-h6">{{currentEdit.cEmail}}</v-card-text>
                    <v-card-subtitle class="text-h5">Phone Number</v-card-subtitle>
                    <v-card-text class="text-h6">{{currentEdit.cPhone}}</v-card-text>
                    <v-btn class="pa-0 align-self-center" :href="'http://'+ currentEdit.cWebsite" width="50%" outlined>Website</v-btn>
                </v-card>
            </v-dialog>
        </div>
    </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
import jsonUs from '../assets/JSON/users.json'
export default Vue.extend({
    data: function() {
        return {
            currentEdit:{
                cEmail:"",
                cPhone:"",
                cWebsite:"",
                isOn: false
            },
            users:[],
            photos: new Array<string>(),
            alertStates:[]
        }
    }, methods:{
        dialogEdit(mail: any, phone: any, website : any) {
            this.currentEdit.cEmail = mail;
            this.currentEdit.cPhone = phone;
            this.currentEdit.cWebsite = mail;
            this.currentEdit.isOn = true;
        }
    }, created() {
            fetch("https://jsonplaceholder.typicode.com/users")
            .then(response => response.json())
            .then(json => {this.users = json})
            .then(json => {
                for(let x in this.users){
                    fetch("https://picsum.photos/200")
                    .then(response => this.photos.push(response.url))
                }
            })
    }
}) 
</script>