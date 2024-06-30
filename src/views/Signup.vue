<script setup>
import $ from 'jquery/dist/jquery.js';
import { initFlowbite } from 'flowbite';
import { onMounted } from 'vue';

let accounts = localStorage.getItem("accounts");
let parsed = JSON.parse(accounts !== null ? accounts : "[]");
let otp = 0;

function generateOtp() {
    otp = Math.floor(Math.random() * 900000) + 100000;
    alert(otp);
}

function signUp() {
    $("#error-message")
        .removeClass("block")
        .addClass("hidden");
    if(password.length < 8 ) {
        alert("Invalid password length, must be at least 8 characters.");
        return;
    }
    
    if($("#otp").val() != otp) {
        $("#error-message")
            .removeClass("hidden")
            .addClass("block");
        return;
    }

    let username = $("#username").val(),
        password = $("#password").val();

    parsed.push([username, btoa(password)]);
    localStorage.setItem("accounts", JSON.stringify(parsed));
    window.location.href = "/home";
}

onMounted(() => initFlowbite())
</script>

<template>
    <div class="p-4" align="center">
        <br/>

        <h1 class="drop-shadow-lg font-black text-2xl">
            <img src="/recipefier.svg" width="128" height="128" /> Recipefier &mdash; Sign-up
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
            </div>

            <p>Have an account already? You can <router-link :to="{ name: 'login' }" class="text-sky-600 underline">log-in</router-link> here.</p>
            <button @click="generateOtp()" data-modal-target="default-modal" data-modal-toggle="default-modal" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign-up</button>
        </div>
    </div>

    <div id="default-modal" tabindex="-1" aria-hidden="true" class="hidden overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full">
        <div class="relative p-4 w-full max-w-2xl max-h-full">
            <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                <div class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600">
                    <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                        Sign-up OTP
                    </h3>
                    <button type="button" class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-hide="default-modal">
                        <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
                        </svg>
                        <span class="sr-only">Close modal</span>
                    </button>
                </div>

                <div class="p-4 md:p-5 space-y-4">
                    <label for="otp" class="block text-sm font-medium text-gray-900">One-time Password</label>
                    <input type="number" id="otp" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 w-full p-2.5" placeholder="One-Time Password (OTP)" />
                    <p class="text-red-600 hidden" id="error-message">Invalid one-time password value.</p>
                </div>

                <div class="flex items-center p-4 md:p-5 border-t border-gray-200 rounded-b dark:border-gray-600">
                    <button @click="signUp()" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2">Sign-up</button>
                </div>
            </div>
        </div>
    </div>
</template>
