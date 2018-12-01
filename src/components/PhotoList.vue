<template lang="html">
    <div class="photo-list">
        <PhotoElement v-for="photo in photos" :key="photo.id" :photo="photo"></PhotoElement>
    </div>
</template>

<script>
    import PhotoElement from './PhotoElement'

    export default {
        name: 'PhotoList',

        components: {
            PhotoElement
        },

        props: {
            photos: {
                type: Array,
                default() {
                    return []
                }
            }
        }
    }
</script>

<style scoped lang="scss">
    .photo-list {
        display:flex;
        justify-content:space-between;
        flex-wrap: wrap;
    }
</style>
