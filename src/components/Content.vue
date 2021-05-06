<template>
    <section class="albums">
        
        <Album :info="album"
        v-for="(album, index) in albumsList" 
        :key="index" />
        
    </section>
</template>

<script>
import axios from "axios";
import Album from "@/components/Album.vue";

export default {
    name: "Content",
    components: {
        Album,
    },
    data() {
        return {
            albumsList: [],
            loading: true,
        };
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
    },
};
</script>

<style scoped lang="scss">
.albums {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 100px 0 20px 0;
    background-color: #1d2d3c;
}
</style>
