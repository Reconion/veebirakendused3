<template>
    <span>
    <button id="add-course-button" class="blue-button" v-on:click="showForm">+</button>
    <span id="add-course" ref="addItem">
        <input class="input" type="text" placeholder="Course title" id="title" v-model="course">
        <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester" v-model="semester">
        <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade" v-model="grade">
        <button class="green-button" id="save-course" @click="addCourses">Save</button>
        <button class="grey-button" id="cancel-course" @click="clear">Cancel</button>
    </span>
    </span>
</template>
<script>


    export default {
        name: 'AddCourse',

        data: () => {
            return{
                course: "",
                semester: null,
                grade: null
            }
        },
        methods: {
            showForm: function () {
                this.$refs['addItem'].style.display = 'inline'
            },
            addCourses: function(){
                this.$emit('addCourse', {title:this.course, semester:this.semester, grade:this.grade})
            },
            clear: function () {
                this.$refs['addItem'].style.display = 'none';
                this.course = "";
                this.semester = null;
                this.grade = null;
            },
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