<template>
    <div class="select">
        <label for="genre-select">Flilter by genre:</label>
        <select name="genre" id="genre-select" v-model="selected" @change="$emit('changed', selected)">
            <option value="all">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'Select',
    data() {
        return {
            selected: 'all',
        }
    }
}
</script>

<style scoped lang="scss">
.select {
    padding: 30px 0;
    background-color: #1d2d3c;
    color: #fff;
    text-align: center;

    label {
        margin-right: 10px;
    }

    select {
        Background-color: #2e3a46;
        color: white;
        outline: none;
        border: 0;
        padding: 5px 10px;
    }

}
</style>