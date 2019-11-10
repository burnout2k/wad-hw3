<template>
    <div>
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
        <tbody v-for="(course, index) in courses" :key="index">
        <tr>
            <td>{{index+1}}</td>
            <td>{{course.title}}</td>
            <td>{{course.semester}}</td>
            <td>{{course.grade}}</td>
        </tr>
        </tbody>
    </table>
    </div>
</template>

<script>
    export default {
        name: "List",
        props: {
            courses: Array,
        }
    }
</script>

<style scoped>

</style>