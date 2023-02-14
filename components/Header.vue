<script setup>
import { onMounted, ref } from 'vue'
import { Dropdown, Popover, Modal } from 'flowbite'
onMounted(() => {
    const screenwidth = ref(0);

    const $btnElement = document.querySelector('#loginBtn')
    const $modalElement = document.querySelector('#loginModal')
    const $closeBtn = document.querySelector('#closeBtn')

    const modalOptions = {
        backdropClasses: 'bg-gray-900 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40'
    }
    // set the dropdown menu element
    const $hamburgerTargetEl = document.getElementById('hamburgerMenu');
    const $popoverTargetE1 = document.getElementById('popoverContent');
    // set the element that trigger the dropdown menu on click
    const $hamburgerTriggerEl = document.getElementById('hamburgerButton');
    const $popoverTriggerE1 = document.getElementById('popoverButton');
    // options with default values
    const hamburderOptions = {
        placement: 'bottom',
        offsetSkidding: 0,
        offsetDistance: 15,
        onHide: () => {
            console.log('hamburger has been hidden');
        },
        onShow: () => {
            console.log('hamburger has been shown');
        }
    };
    const popoverOption = {
        placement: 'bottom',
        triggerType: "hover",
        offset: 10,
        onHide: () => {
            console.log('dropdown has been hidden');
        },
        onShow: () => {
            console.log('dropdown has been shown');
        }
    }
    function updateScreenWidth() {
        screenwidth.value = window.innerWidth;
        if (screenwidth.value > 767) {
            const hamburger = new Dropdown($hamburgerTargetEl, $hamburgerTriggerEl, hamburderOptions);
            hamburger.hide();
        }
    }

    function onScreenResize() {
        window.addEventListener('resize', () => {
            updateScreenWidth();
        })
    }
    if ($hamburgerTargetEl) {
        /*
        * targetEl: required
        * triggerEl: required
        * options: optional
        */
        const hamburger = new Dropdown($hamburgerTargetEl, $hamburgerTriggerEl, hamburderOptions);
        // show the dropdown
        hamburger.hide();
    }
    if ($popoverTargetE1) {
        const popover = new Popover($popoverTargetE1, $popoverTriggerE1, popoverOption);
        popover.hide();
    }
    if ($modalElement) {
        const modal = new Modal($modalElement, modalOptions)
        $btnElement.addEventListener('click', () => modal.toggle())
        $closeBtn.addEventListener('click', () => modal.hide())
    }
    updateScreenWidth();
    onScreenResize();
})

const isShow = ref(false);
const isLogin = ref(true);


</script>
<template>
    <nav class="sticky top-0 z-10 bg-white border-b-[1px] border-[#e4e4e7]">
        <div class="flex flex-wrap items-center justify-between mx-auto px-6 py-3 md:py-0 text-[16px]">
            <div class="flex items-center z-100">
                <a href="#" class="flex items-center">
                    <img src="https://www.auctions.re/public/images/AuctionsRE_02.png?_wwcv=48"
                        class="w-[86px] h-[49px] mr-3" alt="Flowbite Logo" />
                    <div class="hidden md:block md:min-w-[210px] lg:min-w-[400px] min-h-[50px]">
                        <input type="search" id="default-search"
                            class="block box-border w-full min-h-[50px] px-4 text-sm placeholder:text-gray-600 placeholder:text-[16px] border border-gray-300 rounded-[4px] focus:outline-offset-0 focus:outline-none"
                            placeholder="State, County, City, Zip Code..." required>
                    </div>
                </a>
            </div>
            <button type="button" id="hamburgerButton"
                class="z-100 inline-flex items-center p-2 ml-3 text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 "
                aria-controls="navbar-hamburger" aria-expanded="false">
                <span class="sr-only">Open main menu</span>
                <svg class="w-6 h-6" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20"
                    xmlns="http://www.w3.org/2000/svg">
                    <path fill-rule="evenodd"
                        d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
                        clip-rule="evenodd"></path>
                </svg>
            </button>
            <div class="hidden w-full z-100 bg-white" id="hamburgerMenu">
                <ul class="flex flex-col">
                    <li>
                        <button @click="isShow = !isShow"
                            class="flex justify-between items-center w-full text-center py-2 pl-3 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">
                            <span>Buy</span>
                            <svg class="w-5 h-5 ml-1" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20"
                                xmlns="http://www.w3.org/2000/svg">
                                <path fill-rule="evenodd"
                                    d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                    clip-rule="evenodd"></path>
                            </svg></button>
                    </li>
                    <li v-if="isShow">
                        <a href="#"
                            class="block py-2 pl-6 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">All
                            Auctions</a>
                    </li>
                    <li v-if="isShow">
                        <a href="#"
                            class="block py-2 pl-6 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">Bank
                            Owned</a>
                    </li>
                    <li v-if="isShow">
                        <a href="#"
                            class="block py-2 pl-6 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">Signature
                            Seller Auctions</a>
                    </li>
                    <li>
                        <a href="#"
                            class="block py-2 pl-3 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">Sell</a>
                    </li>
                    <li>
                        <a href="#"
                            class="block py-2 pl-3 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">Blog</a>
                    </li>
                    <li>
                        <a href="#"
                            class="block py-2 pl-3 pr-4 font-semibold text-gray-700 rounded hover:bg-gray-100">Alerts</a>
                    </li>
                </ul>
                <div class="w-full px-3">
                    <button type="button" id="loginBtn"
                        class="w-full mt-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded text-sm px-5 py-2.5 text-center mr-3 md:mr-0">Register/Sign
                        In</button>
                </div>
                <div class="w-full my-4 px-3">
                    <input type="search" id="default-search"
                        class="block w-full min-h-[50px] px-4 text-sm placeholder:text-gray-600 placeholder:text-[16px] border border-gray-300 rounded-[4px] focus:outline-offset-0 focus:outline-none"
                        placeholder="State, County, City, Zip Code..." required>
                </div>

            </div>
            <div class="hidden z-100 md:flex flex-wrap justify-between">
                <div class="md:w-auto" id="navbar-multi-level">
                    <ul
                        class="flex flex-col items-center py-3 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white">
                        <li>
                            <button id="popoverButton"
                                class="flex items-center justify-between w-full py-2 pl-3 pr-4 font-medium md:text-[14px] lg:text-[16px] text-black border-b border-gray-100 hover:bg-gray-50 md:hover:bg-transparent md:border-0 md:p-0 md:w-auto">Buy
                                <svg class="w-5 h-5 ml-1" aria-hidden="true" fill="currentColor" viewBox="0 0 20 20"
                                    xmlns="http://www.w3.org/2000/svg">
                                    <path fill-rule="evenodd"
                                        d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                        clip-rule="evenodd"></path>
                                </svg></button>
                            <!-- Dropdown menu -->
                            <div id="popoverContent" role="tooltip"
                                class="z-10 invisible font-normal bg-white divide-y divide-gray-100 px-4 py-2 rounded-[15px] drop-shadow-md">
                                <ul class="py-1 text-sm text-gray-700" aria-labelledby="dropdownLargeButton">
                                    <li>
                                        <a href="#" class="block px-4 py-2 text-[18px] font-semibold text-black">All
                                            Auctions</a>
                                    </li>
                                    <li>
                                        <a href="#" class="block px-4 py-2 text-[18px] font-semibold text-black">Bank
                                            Owned</a>
                                    </li>
                                    <li>
                                        <a href="#"
                                            class="block px-4 py-2 text-[18px] font-semibold text-black">Signature
                                            Seller Auctions</a>
                                    </li>
                                </ul>
                            </div>
                        </li>
                        <li>
                            <a href="#"
                                class="block py-2 pl-3 pr-4 md:text-[14px] lg:text-[16px] text-black rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:p-0">Sell</a>
                        </li>
                        <li>
                            <a href="#"
                                class="block py-2 pl-3 pr-4 md:text-[14px] lg:text-[16px] text-black rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:p-0">Blog</a>
                        </li>
                        <li>
                            <a href="#"
                                class="block py-2 pl-3 pr-4 md:text-[14px] lg:text-[16px] text-black rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:p-0">Alerts</a>
                        </li>
                        <li>
                            <button type="button" id="loginBtn"
                                class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-3 md:mr-0">Register/Sign
                                In</button>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </nav>
    <div id="loginModal" tabindex="-1" aria-hidden="true"
        class="fixed top-0 left-0 right-0 hidden z-50 w-full p-4 overflow-x-hidden overflow-y-auto md:inset-0 h-modal md:h-full">
        <div class="relative w-full md:w-[500px] h-full md:h-auto">
            <!-- Modal content -->
            <div class="relative bg-white p-[24px] rounded-lg shadow dark:bg-gray-700">
                <!-- Modal header -->
                <div class="flex items-start justify-end rounded-t">
                    <button id="closeBtn" type="button"
                        class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd"
                                d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                                clip-rule="evenodd"></path>
                        </svg>
                    </button>
                </div>
                <!-- Modal body -->
                <div class="space-y-6">
                    <div class="flex-col">
                        <div class="flex justify-center">
                            <div @click="isLogin = true"
                                :class="isLogin ? 'cursor-pointer border-b-[3px] p-[12px] m-[12px] text-[18px] border-b-blue-500 text-blue-500' : 'cursor-pointer p-[12px] m-[12px] text-[18px]'">
                                Login
                            </div>
                            <div @click="isLogin = false"
                                :class="!isLogin ? 'cursor-pointer border-b-[3px] p-[12px] m-[12px] text-[18px] border-b-blue-500 text-blue-500' : 'cursor-pointer p-[12px] m-[12px] text-[18px]'">
                                Register
                            </div>
                        </div>
                        <div v-if="isLogin">
                            <div class="flex flex-col p-[8px] mb-[12px]">
                                <form class="space-y-4 md:space-y-6" action="#">
                                    <div>
                                        <label for="email"
                                            class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Email
                                            Address</label>
                                        <input type="email" name="email" id="email"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                            placeholder="name@address.com" required="">
                                    </div>
                                    <div>
                                        <label for="password"
                                            class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Password</label>
                                        <input type="password" name="password" id="password"
                                            placeholder="Enter your password"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                            required="">
                                    </div>
                                    <button type="submit"
                                        class="w-full text-white bg-blue-600 hover:bg-blue-700 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center">Login</button>

                                </form>
                            </div>
                            <div class="mt-[20px] mb-[5px] flex flex-wrap justify-between">
                                <div class="mt-[12px] w-[39%] border-b-[2px] border-[#e0e0e0] h-0">
                                </div>
                                <p class="text-[16px] tracking-normal">
                                    Or login with
                                </p>
                                <div class="mt-[12px] w-[39%] border-b-[2px] border-[#e0e0e0] h-0">
                                </div>
                            </div>
                            <div class="mt-[10px] p-[8px] border-[1px] border-[#e4e4e7] rounded-lg cursor-pointer">
                                <button
                                    class="w-full justify-center px-[16px] hover:border-blue-400 focus:bg-blue-50 active:bg-blue-100">
                                    <div class="flex items-center space-x-4 justify-center">
                                        <img src="https://tailus.io/sources/blocks/social/preview/images/google.svg"
                                            class="w-5" alt="google logo">
                                        <span
                                            class="block w-max font-semibold tracking-wide text-gray-700 text-sm transition duration-300 group-hover:text-blue-600 sm:text-base">Continue
                                            with Google</span>
                                    </div>
                                </button>
                            </div>
                        </div>
                        <div v-else>
                            <div class="flex flex-col p-[8px] mb-[12px]">
                                <form class="space-y-4 md:space-y-6" action="#">
                                    <div>
                                        <label for="name"
                                            class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Name</label>
                                        <input type="text" name="name" id="name"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                            placeholder="Jane Doe" required="">
                                    </div>
                                    <div>
                                        <label for="email"
                                            class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Email
                                            Address</label>
                                        <input type="email" name="email" id="email"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                            placeholder="janedoe@address.com" required="">
                                    </div>
                                    <div>
                                        <label for="password"
                                            class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Password</label>
                                        <input type="password" name="password" id="password"
                                            placeholder="Enter your password"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                            required="">
                                    </div>
                                    <button type="submit"
                                        class="w-full text-white bg-blue-600 hover:bg-blue-700 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center">Sign up</button>

                                </form>
                            </div>
                            <div class="mt-[20px] mb-[5px] flex flex-wrap justify-between">
                                <div class="mt-[12px] w-[37%] border-b-[2px] border-[#e0e0e0] h-0">
                                </div>
                                <p class="text-[16px] tracking-normal">Or register with</p>
                                <div class="mt-[12px] w-[37%] border-b-[2px] border-[#e0e0e0] h-0">
                                </div>
                            </div>
                            <div class="mt-[10px] p-[8px] border-[1px] border-[#e4e4e7] rounded-lg cursor-pointer">
                                <button
                                    class="w-full justify-center px-[16px] hover:border-blue-400 focus:bg-blue-50 active:bg-blue-100">
                                    <div class="flex items-center space-x-4 justify-center">
                                        <img src="https://tailus.io/sources/blocks/social/preview/images/google.svg"
                                            class="w-5" alt="google logo">
                                        <span
                                            class="block w-max font-semibold tracking-wide text-gray-700 text-sm transition duration-300 group-hover:text-blue-600 sm:text-base">Continue
                                            with Google</span>
                                    </div>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>