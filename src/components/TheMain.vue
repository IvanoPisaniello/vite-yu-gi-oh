<script>
import axios from "axios";
import Card from "./Card.vue";
import Loader from "../components/Loader.vue";
import { store } from "../store";
export default {
    components: {
        Loader,
        Card,

    },

    data() {
        return {
            cards: [],
            loading: false,
            cardsCounter: "",
            store,

        }
    },
    methods: {

        fetchCards(newUrl) {
            const url = newUrl ?? "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0"
            this.loading = true;
            axios.get(url).then((response) => {

                setTimeout(() => {
                    this.loading = false;
                }, 1000);
                this.cards = response.data.data;
                console.log(this.cards)
            })

        },






        fetchCounter() {
            const url = "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0"
            axios.get(url).then((response) => {


                this.cardsCounter = response.data.meta;
                console.log(this.cardsCounter)
            })
        },
    },
    mounted() {
        this.fetchCards();
        this.fetchCounter();

    },

    watch: {
        "store.searchArchetype": function (searchArchetype) {
            this.cards = [];

            this.fetchCards(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${searchArchetype}&num=40&offset=0`)
        },
    },
}


</script>


<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="card-counter">
                <p class="text-white p-2">found {{ cardsCounter.current_rows }} cards</p>
            </div>

            <div class="col" v-for="card in cards" :key="card.id">

                <div class="card text-start mb-3">
                    <img class="card-img-top" :src="card.card_images[0].image_url" alt="Title">
                    <div class="card-body">
                        <h4 class="card-title">{{ card.name }}</h4>
                        <p class="card-text">{{ card.archetype }}</p>
                    </div>
                </div>

            </div>
            <Loader v-if="loading"></Loader>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card-counter {
    height: 50px;
    background-color: black;
    width: 97.5%;
}

.container {
    width: 900px;

}

img {
    height: 200px;


}

.card {
    background-color: orange;
    height: 300px;
    min-width: 150px;

    h4 {
        font-size: 1rem;
        text-align: center;
        color: white;
    }

    p {
        font-size: .8rem;
        text-align: center;
    }
}
</style>