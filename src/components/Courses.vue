<template>
    <div id="courses-container" class="tab">
        <List :courses = "courses"/>
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
    import List from "./List";
	import Course from "../models/Course";
    import { bus } from '../main'
    export default {
        name: "Courses",
        components: {List},
        data: function() {
            return {
                realgpa : 0,
                sum : 0,
                isActiveButton: false,
                courses: [
                    new Course("Operation systems", 1, 98),
                    new Course("Software Engineering", 1, 55),
                    new Course("Algorithms and Data Structures", 1, 68),
                    new Course("Introduction to Data Science", 1, 76)
                ]
            };
        },
		methods: {
            swap: function() {
				this.isActiveButton = !this.isActiveButton;
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
				this.gpa();
                bus.$emit('gpa', this.realgpa);
            },
            gpa: function() {
                this.sum = 0;
                for (let i = 0; i < this.courses.length; i++) {
                    if (this.courses[i].grade > 90){
                        this.sum = this.sum + 4;
                    }
                    else if (this.courses[i].grade > 80){
                        this.sum = this.sum + 3;
                    }
                    else if (this.courses[i].grade > 70){
                        this.sum = this.sum + 2;
                    }
                    else if (this.courses[i].grade > 60){
                        this.sum = this.sum + 1;
                    }
                    else if (this.courses[i].grade > 50){
                        this.sum = this.sum + 0.5;
                    }
                }
                this.realgpa = this.sum/this.courses.length;
            },
            mounted(){
                this.gpa();
                bus.$emit('gpa', this.realgpa);
            }

        },
    }
</script>

<style>

</style>