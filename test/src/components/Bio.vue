<template>
    <div>
        {{bio}}
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Bio',
    props: {
        language_id: String
    },
    data() {
        return {
            bio: ''
        }
    },
    mounted() {
        axios.get('http://127.0.0.1:5000/get_bio/' + this.language_id)
        .then(response => {
            this.bio = response.data.bio
        })
        .catch(err => {
            this.bio = err
        });

    }
}
</script>

<style scoped>

</style>

