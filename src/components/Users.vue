<template>
    <div id="profile-container" class="tab active">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{ user.firstname }} {{ user.lastname }}</li>
                    <li id="birthdate">{{ user.birthdate }}</li>
                    <li id="faculty">{{ user.faculty }}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{ user.gpa }}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
	import User from "../models/User";
    export default {
        name: "Users",
		data: function() {
            return {
                isActiveButton: false, user:(new User("John", "Doe", "11/10/1990", "Software Engineering", 2.75))
            };
        }
    }
</script>

<style>

</style>