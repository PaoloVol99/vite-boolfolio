<template>
    <div>
        <p v-for="project in projects" :key="project.id"> {{ project.title }}</p>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        data() {
            return {
                projects: []
            }
        },
        methods: {
            fetchProject() {
                axios.get('http://127.0.0.1:8000/api/projects')
                .then(res => {
                    console.log(res)
                    const { results } = res.data
                    this.projects = results
                })
                .catch(err => {
                    console.log(err)
                })
            }
        }, 
        mounted () {
            this.fetchProject();
        },
    }
</script>

<style lang="scss" scoped>

</style>