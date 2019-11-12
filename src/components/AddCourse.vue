<template>
    <span>
    <button id="add-course-button" class="blue-button" v-on:click="showForm">+</button>
    <span id="add-course" ref="addItem">
        <input class="input" type="text" placeholder="Course title" id="title">
        <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
        <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
        <button class="green-button" id="save-course">Save</button>
        <button class="grey-button" id="cancel-course">Cancel</button>
    </span>
    </span>
</template>
<script>
    export default {
        name: 'AddCourse',
        props: {
        },
        methods: {
            showForm: function () {
                this.$refs['addItem'].style.display = 'inline'
            }
        }
    }
</script>

<style scoped>
.blue-button {
background-color: #2196F3;
color: #ffffff;
border: none;
padding: 10px 20px;
}

.green-button {
background-color: #69f378;
color: #ffffff;
border: none;
padding: 10px 10px;
}

.grey-button {
background-color: #e1e8e6;
color: #ffffff;
border: none;
padding: 10px 20px;
}

.input {
border: 1px solid #cccccc;
padding: 10px 20px;
min-width: 135px;
}

#add-course {
display: none;

}
</style>