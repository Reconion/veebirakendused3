<template>
    <span>
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
        <CoursesTable v-bind:courses="courses"/>
        </table>
        <br>
        <br>
        <div>

            <AddCourse />

        </div>
    </span>
</template>
<script>
    import AddCourse from './AddCourse'
    import CoursesTable from "./CoursesTable";

    export default {
        name: 'app',
        components: {
            CoursesTable,
            AddCourse,
        },
        props: {
            courses: Array
        },
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    header {
        padding: 20px;
        background-color: #2196F3;
        color: #ffffff;
        text-align: center;
        margin-bottom: 10px;
        height: 60px;
    }

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile #gpa strong {
        position: absolute;
        width: 100%;
        height: 60px;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        margin: auto auto;
        font-size: 60px;
        line-height: 60px;
        text-align: center;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }
</style>
