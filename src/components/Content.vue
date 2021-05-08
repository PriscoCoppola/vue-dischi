<template>
    <section class="albums">
        <div class="filter">
            <Select @changed="filteredGenre" />
        </div>
        
        <div class="box">
            <Album :info="album"
            v-for="(album, index) in newAlbumsList"
            :key="index" />
        </div>
        
    </section>
</template>

<script>
import axios from "axios";
import Album from "@/components/Album.vue";
import Select from "@/components/Select.vue";

export default {
    name: "Content",
    components: {
        Album,
        Select,
    },
    data() {
        return {
            albumsList: [],
            loading: true,
            genreSelected: 'all',
        };
    },
    computed: {
        newAlbumsList() {
            if (this.genreSelected === 'all') {
                return this.albumsList;
            }

            return this.albumsList.filter( album => {
                return album.genre.toLowerCase() === this.genreSelected.toLowerCase()
            })
        }
    },
    created() {
        this.getAlbums();
    },
    methods: {
        getAlbums() {
            axios
                .get("https://flynn.boolean.careers/exercises/api/array/music")
                .then((res) => {
                    this.albumsList = res.data.response;
                    this.loading = false;
                })
                .catch((err) => {
                    console.log("Error", err);
                });
        },
        filteredGenre(select) {
            this.genreSelected = select;
            console.log(this.genreSelected);
        },
    },
};
</script>

<style scoped lang="scss">
.box {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 20px 0;
    background-color: #1d2d3c;
}
</style>
