<template>
    <div>
        <table class="table">
            <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">Name</th>
                <th scope="col">Age</th>
                <th scope="col">Job</th>
                <th scope="col">Edit</th>
            </tr>
            </thead>
            <tbody>
            <template v-for="person in people">
                <tr :class="isEdit(person.id) ? 'd-none' : '' ">
                    <th scope="row">{{ person.id }}</th>
                    <td>{{ person.name }}</td>
                    <td>{{ person.age }}</td>
                    <td>{{ person.job }}</td>
                    <td><a href="#" @click.prevent="changeEditPersonId(person.id)"
                           class="btn btn-success">Edit</a></td>
                </tr>
                <tr :class="isEdit(person.id) ? '' : 'd-none' ">
                    <th scope="row">{{ person.id }}</th>
                    <td><input type="text" v-model="person.name" class="form-control w-50"></td>
                    <td><input type="number" v-model="person.age" class="form-control w-50"></td>
                    <td><input type="text" v-model="person.job" class="form-control w-50"></td>
                    <td><a href="#" @click.prevent="updatePerson(person.id, person.name, person.age, person.job)" class="btn btn-success">Update</a></td>
                </tr>
            </template>

            </tbody>
        </table>
    </div>
</template>

<script>


export default {
    name: "IndexComponent",

    data() {
        return {
            people: null,
            editPersonId: null,
            name: null,
            age: null,
            job: null
        }
    },

    mounted() {
        this.getPeople()
    },

    methods: {
        getPeople() {
            axios.get('/api/people')
                .then(res => {
                    this.people = res.data
                })
        },

        updatePerson(id, name, age, job){
            this.editPersonId = null
            this.name = name
            this.age = age
            this.job = job
            console.log(this.name, this.age, this.job);
            axios.patch(`/api/people/${id}`, {name: this.name, age: this.age, job: this.job})
                .then(res => {
                    console.log(res);
                })
        },

        changeEditPersonId(id) {
            this.editPersonId = id
        },

        isEdit(id) {
            return this.editPersonId === id
        }
    }
}
</script>

<style scoped>

</style>
