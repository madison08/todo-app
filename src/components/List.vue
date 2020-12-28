<template>
    <div>
        <div class="bloc-bloc">

        
            <div>
                <h2>Liste de vehicule</h2>
                <p>Ajouter des vehicules</p>
                <p>{{ voitures.length > 0 ? 'Cochez la case pour acheter ' : ''  }}</p>

                <ul class="li_element">
                    <li v-for="(voiture, index) in voitures" v-bind:key="index"> {{ voiture }} <svg @click="remove(index)" class="delete" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='green'><path d="M0 0h24v24H0V0zm0 0h24v24H0V0z" fill="none"/><path d="M16.59 7.58L10 14.17l-3.59-3.58L5 12l5 5 8-8zM12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8z"/></svg></li>
                </ul>
                <br>
                <form action="">
                    <input v-model="voiture" type="text" placeholder="Entrez une voiture">
                    <button @click.prevent="add()">Ajouter</button>
                </form>
                
            </div>
            <div>
                <ul class="li_element voiturA">
                    <h2>{{ voituresAcheters.length }} voiture{{ voituresAcheters.length > 1 ? 's' : ' '  }} acheter </h2>
                    <li v-for="(voituresAcheter, index2) in voituresAcheters" v-bind:key="index2"> {{ voituresAcheter }} <svg @click="re_add(index2)" class="delete" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24" fill='red'><path d="M0 0h24v24H0z" fill="none"/><path d="M12 2C6.47 2 2 6.47 2 12s4.47 10 10 10 10-4.47 10-10S17.53 2 12 2zm5 13.59L15.59 17 12 13.41 8.41 17 7 15.59 10.59 12 7 8.41 8.41 7 12 10.59 15.59 7 17 8.41 13.41 12 17 15.59z"/></svg></li>
                </ul>

            </div>
        </div>

        
        
    </div>
</template>

<script>
    export default{
        name: 'list',


        data: function(){
            return{
                voiture: '',
                voitures: [],
                voituresAcheters: [],
                // pluriel: 's'
                // voitureA: ''
            }
        },

        methods: {
            add: function(){

                if(this.voiture != '' && this.voiture != undefined){

                    this.voitures.push(this.voiture)
                    this.voiture = ''
                }else{
                    alert('Ecrivez le nom de la voiture avant validation')
                }


                
            },
            remove: function(index){

                this.voituresAcheters.push(this.voitures[index])
                this.voitures.splice(index,1)
                // if(this.voituresAcheters.length > 1){
                //     this.pluriel = 's'
                // }
            },
            re_add: function(index2){
                this.voitures.push(this.voituresAcheters[index2])
                this.voituresAcheters.splice(index2,1)
            }
            
            
        } 
    }

</script>

<style  scoped>
    input{
        padding: 7px;
        border: 1px solid #e2e2e2;
    }
    button{
        padding: 7px;
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
        /* display: inline-block; */
        /* background-color: green; */
        position: absolute;
        right: 0px;
    }
    .bloc-bloc p{
        line-height: 7px;
    }
    .bloc-bloc{
        display: flex;
        width: 70%;
        justify-content: space-around;
        border: 1px solid #e2e2e2;
        padding: 30px;
    }

    @media(max-width: 711px){
        .bloc-bloc{
            flex-direction: column;
        }

    }
</style>