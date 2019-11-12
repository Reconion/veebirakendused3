<template>
    <tbody>
    <tr v-for="(course, index) in courses" v-bind:key="index">
        <td>{{course.id}}</td>
        <td>{{course.title}}</td>
        <td>{{course.semester}}</td>
        <td>{{course.grade}}</td>
    </tr>
    </tbody>
</template>

<script>
    export default {
        name: "CoursesTable",
        props: {
            courses: Array
        },
    }
</script>

<style scoped>

</style>