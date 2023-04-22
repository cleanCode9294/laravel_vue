<template>
    <div class="m-5">
        <create-component/>
        <index-component/>
    </div>

<!--    <table class="table">
        <thead>
        <tr>
            <th scope="col">#</th>
            <th scope="col">First</th>
            <th scope="col">Last</th>
            <th scope="col">Handle</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <th scope="row">1</th>
            <td>Mark</td>
            <td>Otto</td>
            <td>@mdo</td>
        </tr>
        </tbody>
    </table>-->
</template>

<script>

import createComponent from "@/components/CreateComponent.vue";
import indexComponent from "@/components/IndexComponent.vue";

export default {
    name: "PostComponent",
    components: {
        createComponent,
        indexComponent
    },

    data() {

    },

    computed: {},

    mounted() {

    },

    methods: {

    }

}
</script>

<style scoped>

</style>
