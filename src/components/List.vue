<template>
    <div>
        <form action="">
            <input v-model="tache" type="text" placeholder="ajouter une tache">
            <button @click.prevent="add()">Ajouter</button>
        </form>
        <div class="bloc-bloc">

        
            <div>
                <h2>To do</h2>
                
                <!-- <p>{{ voitures.length > 0 ? 'Cochez la case pour acheter ' : ''  }}</p> -->

                <ul class="li_element">
                    <li v-for="(tache, index) in taches" v-bind:key="index"> {{ tache }} <svg @click="addDo(index)" class="delete" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='green'><path d="M0 0h24v24H0V0zm0 0h24v24H0V0z" fill="none"/><path d="M16.59 7.58L10 14.17l-3.59-3.58L5 12l5 5 8-8zM12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"/></svg>  <svg @click="addPro(index)" class="delete1" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='orange'><path d="M0 0h24v24H0V0z" fill="none"/><path d="M11 15h2v2h-2zm0-8h2v6h-2zm.99-5C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"/></svg></li>
                </ul>
                <br>
                
                
            </div>
            <div>
                <h2>In progress</h2>
                <ul class="li_element">
                    <li v-for="(tache, indexPro) in tachesProg" v-bind:key="indexPro"> <span class="inprog"> {{ tache }} </span> <svg @click="addProToDo(indexPro)" class="delete" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='green'><path d="M0 0h24v24H0V0zm0 0h24v24H0V0z" fill="none"/><path d="M16.59 7.58L10 14.17l-3.59-3.58L5 12l5 5 8-8zM12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"/></svg>  <svg @click="RemProToDo(indexPro)" class="delete1" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='red'><path d="M0 0h24v24H0z" fill="none"/><path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"/></svg>  </li>
                </ul>

            </div>
            <div>
                <h2>Done</h2>
                <ul class="li_element">
                    <li v-for="(tache, indexDo) in tachesDo" v-bind:key="indexDo"> <span style="text-decoration: line-through;"> {{ tache }} </span> <svg @click="RemDoToPro(indexDo)" class="delete1" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='red'><path d="M0 0h24v24H0z" fill="none"/><path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"/></svg> <svg @click="RemDoToProg(indexDo)" class="delete" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='orange'><path d="M0 0h24v24H0V0z" fill="none"/><path d="M11 15h2v2h-2zm0-8h2v6h-2zm.99-5C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"/></svg></li>
                </ul>
            </div>
        </div>

        
        
    </div>
</template>

<script>
// import func from '../../vue-temp/vue-editor-bridge'
    export default{
        name: 'list',


        data: function(){
            return{
                tache: '',
                tacheEl: '',
                taches: [],
                tachesProg: [],
                tachesDo: []
            }
        },

        methods: {
            add: function(){

                if(this.tache != '' && this.tache != undefined){

                    this.taches.push(this.tache)
                    this.tache = ''
                }else{
                    alert('Ecrivez le nom de la voiture avant validation')
                }

            },
            addPro: function(index){
                this.tachesProg.push(this.taches[index])
                this.taches.splice(index,1)
            },
            addDo: function(index){
                this.tachesDo.push(this.taches[index])
                this.taches.splice(index,1)
            },
            addProToDo: function(indexPro){
                this.tachesDo.push(this.tachesProg[indexPro])
                this.tachesProg.splice(indexPro,1)
            },
            RemProToDo: function(indexPro){
                this.taches.push(this.tachesProg[indexPro])
                this.tachesProg.splice(indexPro,1)

            },
            RemDoToPro: function(indexDo){
                this.taches.push(this.tachesDo[indexDo])
                this.tachesDo.splice(indexDo,1)
            },
            RemDoToProg: function(indexDo){
                this.tachesProg.push(this.tachesDo[indexDo])
                this.tachesDo.splice(indexDo,1)
            },
            tacheEdit: function(index){
                this.tacheEl = this.taches[index]
            }
            // remove: function(index){

            //     this.voituresAcheters.push(this.voitures[index])
            //     this.voitures.splice(index,1)
            //     // if(this.voituresAcheters.length > 1){
            //     //     this.pluriel = 's'
            //     // }
            // },
            // re_add: function(index2){
            //     this.voitures.push(this.voituresAcheters[index2])
            //     this.voituresAcheters.splice(index2,1)
            // }
            
            
        } 
    }

</script>

<style  scoped>

    .bloc-bloc div h2{
        background-color: #e2e2e2;
        padding: 15px;
    }

    .bloc-bloc div:nth-child(1){
        background-color: #fff;
        padding-left: 10px;
        padding-right: 10px;
        width: 30.3%;
        /* height: 100px;
        width: 100px; */
    }
    .bloc-bloc div:nth-child(2){
        background-color: #fff;
        padding-left: 10px;
        padding-right: 10px;
        width: 30.3%;
    }
    .bloc-bloc div:nth-child(3){
        background-color: #fff;
        padding-left: 10px;
        padding-right: 10px;        
        width: 30.3%;
    }
    .bloc-bloc div:nth-child(1) input{
        border: none;
        cursor: default;
    }
    input{
        padding: 10px;
        border: 1px solid #e2e2e2;
    }
    form{
        margin-bottom: 25px;
        margin-left: 25px;
    }
    button{
        padding: 13px;
        background-color: #e2e2e2;
        margin-left: 2px;
        cursor: pointer;
    }
    button{
        padding: 7px;
        margin-left: 5px;
        border: none;
    }
    .li_element{
        /* width: 80%; */
        margin: 0 auto;
        margin-left: 0px;
        padding-left: 0px;
        position: relative;
        
    }
    .li_element li{
        display: block;
        line-height: 20px;
        background-color: #fff;
        padding: 15px;
        border-top: 2px solid #e2e2e2;
    }
    .voiturA{
        margin-top: 25px;
        background-color: #000;
        color: #fff;
        padding: 10px;
    }
    .voiturA h2{
        text-decoration: underline;
    }
    .delete{
        width: 30px;
        height: 23px;
        cursor: pointer;
        /* display: inline-block; */
        /* background-color: green; */
        position: absolute;
        right: 30px;
    }
    .delete1{
        position: absolute;
        right: 10px;
        cursor: pointer;
    }

    .bloc-bloc p{
        line-height: 7px;
    }
    .bloc-bloc{
        display: flex;
        width: 90%;
        justify-content: space-around;
        border: 1px solid #e2e2e2;
        padding: 30px;
    }

    @media(max-width: 711px){
        .bloc-bloc{
            flex-direction: column;
        }

    }

    .inprog{
        animation: 1s prog;
    }
    @keyframes prog {
        0%{
            position: relative;
            top: 20px;
        }
        100%{
            position: relative;
            top: 0px;
        }
    }
</style>