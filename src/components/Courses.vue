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
            <tbody>
            <tr>
                <td>1</td>
                <td>Agile software development</td>
                <td>1</td>
                <td>82</td>
            </tr>
            <tr>
                <td>2</td>
                <td>System modeling</td>
                <td>1</td>
                <td>85</td>
            </tr>
            <tr>
                <td>3</td>
                <td>Object-oriented programming</td>
                <td>2</td>
                <td>99</td>
            </tr>
            <tr>
                <td>4</td>
                <td>Estonian language Level A2</td>
                <td>2</td>
                <td>65</td>
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
                                <button class="green-button" id="save-course">Save</button>
                                <button class="grey-button" id="cancel-course" v-on:click="cancel">Cancel</button>
                            </span>
        </div>
    </div>
</template>

<script>
    //import Course from '../models/Course'
    export default {
        name: "Courses",
		data: function() {
            return {
                isActiveButton: false,
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
				
            }
        }
    }
</script>

<style>

</style>