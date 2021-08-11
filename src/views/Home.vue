<template>
    <v-container>
        <h2 class="white--text text-left">Welcome to the main page!</h2>
        <v-divider dark class="my-2"></v-divider>
        <div class="pb-2"> 
            <h3 class="white--text text-left">Top Today</h3>
            <div class="d-flex flex-row nigga" style="overflow-x:auto;">
             <div v-for="items, index of itemlist" :key="index" class="mx-1 pa-2 rounded d-flex flex-column" style="background:#252525; width:200px; min-width:200px">
                 <v-avatar size="100" class="align-self-center"><v-img :src="items.avatar"/></v-avatar>
                 <p class="white--text text-left text-h5 my-1">{{items.name}}</p>
                 <p class="white--text text-center">{{items.desc}}</p>
                 <v-btn v-if="items.hasContact" color="success" class="mt-auto">Contact</v-btn>
             </div>
            </div>
            <v-divider dark class="my-2"></v-divider>
            <!-- Registro, no tocar-->
            <v-row>
                <v-col cols="8">
                    <v-form style="background:#252525;" class="pa-3">
                        <h2 class="white--text">Registro</h2>
                        <div class="d-inline-flex">
                            <v-text-field label="Name" class="mx-1" v-model="currentEdit.name" dark></v-text-field>
                            <v-text-field label="Avatar (URL)" class="mx-1" v-model="currentEdit.avatar" dark></v-text-field>
                        </div>
                        <v-textarea label="Description" no-resize v-model="currentEdit.desc" dark/>
                        <v-switch v-model="currentEdit.hasContact" label="Do you want people to contact you?" dark></v-switch>
                        <v-btn dark @click="pushInfo">Enviar</v-btn>
                    </v-form>
                </v-col>
            </v-row>
        </div>
    </v-container>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data: function() {
        return {
            currentEdit:{
                name:"",
                avatar:"",
                desc:"",
                hasContact:false
            },
            itemlist:[
                {
                    name: "Creisi",
                    avatar:"https://i.imgflip.com/4iqmth.png",
                    desc:"Likes fruit, likes your mom and also likes themselves",
                    hasContact:false
                },
                {
                    name: "Akko",
                    avatar:"https://cdn.discordapp.com/avatars/484158363475771413/5a9d32d919c68de2859552a4950a7897.png?size=512",
                    desc:"Pretty dumb, but still lovable, always a good thing to hang out with her",
                    hasContact:false
                },
                {
                    name:"Maya",
                    avatar:"https://cdn.discordapp.com/attachments/798228676553867277/873778780370534401/E8N5y5WUYAEMZJO.png",
                    desc:"Loves burgers, loves Nick and also loves me (webdev)",
                    hasContact:false
                },
                {
                    name:"Phoenix Wright",
                    avatar:"https://cdn.discordapp.com/attachments/798228676553867277/873778609255493642/unknown.png",
                    desc:"Skilled (and sexy) lawyer, pretty good at his job",
                    hasContact:true
                }
            ]
        }
    }, methods:{
        pushInfo(){
            this.itemlist.push(this.currentEdit);
            this.currentEdit = {
                name:"",
                avatar:"",
                desc:"",
                hasContact:false
            };
        }
    }
}) 
</script>