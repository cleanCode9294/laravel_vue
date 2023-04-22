<template>
    <div class="w-25">
        <div class="mb-3">
            <input type="text" v-model="name" class="form-control" id="name" placeholder="Name">
        </div>
        <div class="mb-3">
            <input type="number" v-model="age" class="form-control" id="age" placeholder="Age">
        </div>
        <div class="mb-3">
            <input type="text" v-model="job" class="form-control" id="job" placeholder="Job">
        </div>
        <div class="mb-3">
            <input @click.prevent="addPerson" class="btn btn-primary" value="Добавить">
        </div>
    </div>
</template>

<script>


export default {
    name: "CreateComponent",

    data() {
        return {
            name: null,
            age: null,
            job: null,
        }
    },

    methods: {
        addPerson() {
            axios.post('/api/people', {name: this.name, age: this.age, job: this.job})
                .then(res => {
                    this.name = null
                    this.age = null
                    this.job = null
                    console.log(res)
                })
        }
    }
}
</script>

<style scoped>

</style>
