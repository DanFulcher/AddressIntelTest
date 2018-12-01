<template lang="html">
    <div class="photo-element">
        <div class="photo-element__image-holder">
            <img :src="src" :alt="alt" @click="onImgClick">
        </div>
        <button type="button" @click="onBtnClick" :class="this.photo.liked_by_user ? 'liked' : '' "><img src="../assets/like.svg" /></button>
    </div>
</template>

<script>
    export default {
        name: 'PhotoElement',

        props: {
            photo: {
                type: Object,
                required: true
            },

            size: {
                type: String,
                default: 'regular'
            }
        },

        computed: {
            src() {
                return this.photo.urls[this.size]
            },
            alt() {
                return this.photo.description
            },
        },

        methods: {
            onImgClick() {
                this.$router.push({name: 'Photo', params: { id: this.photo.id }})
            },

            onBtnClick() {
                this.photo.liked_by_user = !this.photo.liked_by_user
            }
        }
    }
</script>

<style scoped lang="scss">
    .photo-element {
        display:flex;
        flex-direction: column;
        flex-basis:33%;
        max-width:100%;
        margin-bottom: 20px;
        position:relative;
        &__image-holder {
            overflow:hidden;
            img {
                width:100%;
                height:500px;
                display:block;
                object-fit:cover;
                transform:scale(1);
                transition:transform 5s;
                &:hover {
                    transform:scale(1.1);
                }
            }
        }
        button {
            -webkit-appearance: none;
            background:none;
            text-transform: capitalize;
            padding:1rem;
            cursor:pointer;
            outline:none;
            color:#fff;
            position:absolute;
            bottom:10px;
            right:10px;
            border-radius:50%;
            border:2px solid #20d404;
            transition:background .5s;
            img {
                width:15px;
            }
            &.liked {
                background:#20d404;
            }
        }
    }
</style>