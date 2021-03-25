<template>
    <div class="ml-4 relative flex-shrink-0">
        <div>
            <button @click="isOpen = !isOpen" type="button"
                    class="bg-gray-800 rounded-full flex text-sm text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white"
                    id="user-menu" aria-expanded="false" aria-haspopup="true">
                <span class="sr-only">Open user menu</span>
                <img class="h-8 w-8 rounded-full"
                     src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixqx=USZW29LMHa&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
                     alt="">
            </button>
        </div>

        <transition
            enter-from-class="transform opacity-0 scale-95"
            enter-active-class="transition ease-out duration-100"
            enter-to-class="transform opacity-100 scale-100"
            leave-from-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75"
            leave-to-class="transform opacity-0 scale-95">

            <div v-if="isOpen" class="origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg py-1 bg-white ring-1 ring-black ring-opacity-5 focus:outline-none"
                 role="menu" aria-orientation="vertical" aria-labelledby="user-menu">
                <a v-for="link in profileLinks"
                   href="#"
                   class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100"
                   role="menuitem">
                    {{ link.displayName }}
                </a>
            </div>
        </transition>
    </div>
</template>

<script>
    export default {
        name: "ProfileDropdownComponent",

        data() {
            return {
                isOpen: false
            }
        },

        props: {
            profileLinks: Array
        }
    }
</script>

