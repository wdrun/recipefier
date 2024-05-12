<script setup>
import $ from 'jquery/dist/jquery.js';

function login() {
    let username = $("#username").val(),
        password = $("#password").val();
    let accounts = localStorage.getItem("accounts");

    $("#error-message")
            .removeClass("block")
            .addClass("hidden");

    if(accounts == null) {
        $("#error-message")
            .removeClass("hidden")
            .addClass("block");
        return;
    }

    accounts = JSON.parse(accounts);
    accounts.forEach(element => {
        if(element[0] == username && element[1] == btoa(password))
            location.href = "/home";
    });

    $("#error-message")
        .removeClass("hidden")
        .addClass("block");
}
</script>

<template>
    <div class="p-4" align="center">
        <br/>

        <h1 class="drop-shadow-lg font-black text-2xl">
            <img src="/recipefier.svg" width="128" height="128" /> Recipefier &mdash; Log-in
        </h1>
        <br/>

        <div class="grid gap-4 mb-6 lg:w-2/5" align="left">
            <div>
                <label for="username" class="block mb-2 text-sm font-medium text-gray-900">Username: </label>
                <input type="text" id="username" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 w-full p-2.5" placeholder="Username" />
            </div>

            <div>
                <label for="password" class="block mb-2 text-sm font-medium text-gray-900">Password: </label>
                <input type="password" id="password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 w-full p-2.5" placeholder="Password" />

                <p class="text-red-600 hidden" id="error-message">Invalid username and/or password.</p>
            </div>

            <p>No account yet? You can <router-link :to="{ name: 'signup' }" class="text-sky-600 underline">sign-up</router-link> here.</p>
            <button @click="login()" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Login</button>
        </div>
    </div>
</template>
