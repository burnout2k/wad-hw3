<template>
    <div id="courses-container" class="tab">
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
        <br>
        <br>
        <div>
            <button id="add-course-button" v-on:click="swap" class="blue-button">+</button>
            <span :id="[ isActiveButton ? 'add-course active' : 'add-course' ]">
                                <input class="input" type="text" placeholder="Course title" id="title" v-model='title'>
                                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester" v-model='semester'>
                                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade" v-model='grade'>
                                <button class="green-button" id="save-course" v-on:click="addNewCourse">Save</button>
                                <button class="grey-button" id="cancel-course" v-on:click="cancel">Cancel</button>
                            </span>
        </div>
    </div>
</template>

<script>
	import Course from "../models/Course";
    export default {
        name: "Courses",
		data: function() {
            return {
                isActiveButton: false,courses: [
                    new Course("Operation systems", 1, 98),
                    new Course("Software Engineering", 1, 55),
                    new Course("Algorithms and Data Structures", 1, 68),
                    new Course("Introduction to Data Science", 1, 76)
                ]
            };
        },
		methods: {
            swap: function() {
				if(this.isActiveButton== false){
					this.isActiveButton = true;
				}else{
				this.isActiveButton = false;
				}
            },
			cancel: function() {
				this.isActiveButton = false;
				this.title = '';
				this.semester = '';
				this.grade = '';
				
            },
			addNewCourse: function(){
				var course = new Course(this.title, this.semester, this.grade);
				this.courses.push(course);
				this.cancel();
			}
        }
    }
</script>

<style>

</style>