<template>
    <div class="album">
        <div class="image">
            <img :src="info.poster" :alt="info.title">
        </div>
        <div class="title">{{ info.title }}</div>
        <div class="artist">{{ info.author }}</div>
        <div class="year">{{ info.year }}</div>
        <div class="genre">{{ info.genre }}</div>
    </div>
</template>

<script>
export default {
    name: "Album",
    props: ['info']
};
</script>

<style scoped lang="scss">
.album {
    display: flex;
    flex-direction: column;
    flex-basis: calc(100% / 8 - 60px);
    width: 140px;
    padding: 20px;
    margin: 10px 30px;
    background-color: #2e3a46;
    text-align: center;

    .image {
        width: 100%;
        height: 150px;

        img {
            width: 100%;
            height: 100%;
        }
    }

    .title {
        padding: 20px 0;
        text-transform: uppercase;
        color: #fff;
    }

    .artist {
        color: #7b7b7d;
    }

    .year {
        padding: 10px 0;
        color: #7b7b7d;
    }

    .genre {
        color: #fff;
    }
}
</style>
