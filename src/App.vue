<!-- 1 COMPONENT -->
<template>
    <main id="app">
        <Header/>
        <section id="container">
            <section id="main">
                <div class="content">
                    <div id="profile-container" ref="profile-container" class="tab active">
                        <div id="profile">
                            <div class="avatar">
                                <img src="./assets/me.png" id="picture" alt="My picture">
                            </div>
                            <div class="info">
                                <ul>
                                    <li id="name">John Doe</li>
                                    <li id="birthdate">11/10/1990</li>
                                    <li id="faculty">Software Engineering</li>
                                </ul>
                            </div>
                            <div id="gpa">
                                <strong>{{this.getGpa()}}</strong>
                            </div>
                            <div class="clear-fix"></div>
                        </div>
                    </div>
                    <div id="courses-container" ref="courses-container" class="tab">
                    <CourseTab v-bind:courses="courses" v-on:addCourse="addCourse($event)"/>
                    </div>
                </div>
                <div class="controls">
                    <button id="profile-button" ref="profile-button" class="pill active" @click="toggle('profile')">Profile</button>
                    <button id="courses-button" ref="courses-button" class="pill" @click="toggle('courses')">Courses</button>
                </div>
            </section>
        </section>
        <Footer/>
    </main>
</template>

<!-- 2 COMPONENT -->
<script>
    import CourseTab from './components/CoursesTab'
    import Header from "./components/Header";
    import Footer from "./components/Footer";

    export default {
        name: 'app',
        components: {
            Footer,
            Header,
            CourseTab
        },
        data () {
            return {
                courses: [
                    {
                        id: 1,
                        title: 'Agile software development',
                        semester: 1,
                        grade: 82
                    },
                    {
                        id: 2,
                        title: 'System modeling',
                        semester: 1,
                        grade: 85
                    },
                    {
                        id: 3,
                        title: 'Object-oriented programming',
                        semester: 2,
                        grade: 99
                    },
                    {
                        id: 4,
                        title: 'Estonian language Level A2',
                        semester: 2,
                        grade: 65
                    },
                ],
            }
        },
        methods: {
            toggle: function (element_to_show) {
                if (element_to_show === ('profile')) {
                    this.$refs['courses-container'].classList.remove('active');
                    this.$refs['courses-button'].classList.remove('active');
                    this.$refs['profile-container'].classList.add('active');
                    this.$refs['profile-button'].classList.add('active');
                } else {
                    this.$refs['profile-container'].classList.remove('active');
                    this.$refs['profile-button'].classList.remove('active');
                    this.$refs['courses-container'].classList.add('active');
                    this.$refs['courses-button'].classList.add('active');
                }
            },
            addCourse: function (data) {
                this.courses.push({id:this.courses.length+1, title: data.title, semester: data.semester, grade: data.grade});
            },
            getGpa: function () {
                let gradeCount = 0;
                for(let i = 0; i < this.courses.length; i++){
                    let current = this.courses[i].grade;
                    if(current > 89){
                        gradeCount += 4;
                    }
                    else if(current < 90 && current > 79){
                        gradeCount += 3;
                    }
                    else if(current < 80 && current > 69){
                        gradeCount += 2;
                    }
                    else if(current < 70 && current > 59){
                        gradeCount += 1;
                    }
                    else if(current < 60 && current > 49){
                        gradeCount += 0.5;
                    }
                }
                let gpa = gradeCount/this.courses.length;
                return gpa;
            }
        }
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

    .clear-fix {
        clear: both;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    #profile {
        border-bottom: 1px dashed #a7a7a7;
        padding-bottom: 10px;
        margin-bottom: 10px;
    }

    #profile div:not(.clear-fix) {
        height: 190px;
        float: left;
        position: relative;
    }

    #profile .avatar {
        width: 35%;
        text-align: center;
    }

    #profile .avatar img {
        width: 180px;
    }

    #profile .info {
        width: 45%;
    }

    #profile #gpa {
        width: 20%;
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

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
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

    .content .tab {
        display: none;
    }

    .content .tab.active {
        display: block;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }
</style>
