<template>
    <div>
        <nav class="bg-gray-800">
            <div class="max-w-7xl mx-auto px-2 sm:px-4 lg:px-8">
                <div class="relative flex items-center justify-between h-16">
                    <div class="flex items-center px-2 lg:px-0">
                        <div class="flex-shrink-0">
                            <AppLogo/>
                        </div>

                        <div class="hidden lg:block lg:ml-6">
                            <div class="flex space-x-4">
                                <MenuLinks/>
                            </div>
                        </div>
                    </div>

                    <div class="flex-1 flex justify-center px-2 lg:ml-6 lg:justify-end">
                        <div class="max-w-lg w-full lg:max-w-xs">
                            <label for="search" class="sr-only">Search</label>

                            <div class="relative">
                                <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                                    <SearchIcon class="h-5 w-5 text-gray-400"/>
                                </div>

                                <input id="search" name="search"
                                       class="block w-full pl-10 pr-3 py-2 border border-transparent rounded-md leading-5 bg-gray-700 text-gray-300 placeholder-gray-400 focus:outline-none focus:bg-white focus:border-white focus:ring-white focus:text-gray-900 sm:text-sm"
                                       placeholder="Search" type="search">
                            </div>
                        </div>
                    </div>

                    <div class="flex lg:hidden">
                        <button @click="isOpen = !isOpen" type="button"
                                class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
                                aria-controls="mobile-menu" aria-expanded="false">
                            <span class="sr-only">Open main menu</span>
                            <MenuIcon v-if="!isOpen" class="block h-6 w-6"/>
                            <XIcon v-else class="block h-6 w-6"/>
                        </button>
                    </div>

                    <div class="hidden lg:block lg:ml-4">
                        <div class="flex items-center">
                            <button class="flex-shrink-0 bg-gray-800 p-1 rounded-full text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                                <span class="sr-only">View notifications</span>

                                <BellIcon class="h-6 w-6"/>
                            </button>

                            <ProfileDropdownComponent :profile-links="profileLinks"/>
                        </div>
                    </div>
                </div>
            </div>

            <div v-if="isOpen" class="lg:hidden" id="mobile-menu">
                <div class="px-2 pt-2 pb-3 space-y-1">
                    <MenuLinks/>
                </div>
                <div class="pt-4 pb-3 border-t border-gray-700">
                    <div class="flex items-center px-5">
                        <div class="flex-shrink-0">
                            <AppLogoCompact/>
                        </div>

                        <div class="ml-3">
                            <div class="text-base font-medium text-white">{{ $page.props.user.name }}</div>
                            <div class="text-sm font-medium text-gray-400">{{ $page.props.user.email }}</div>
                        </div>

                        <button class="ml-auto flex-shrink-0 bg-gray-800 p-1 rounded-full text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-800 focus:ring-white">
                            <span class="sr-only">View notifications</span>

                            <BellIcon class="h-6 w-6"/>
                        </button>
                    </div>
                    <div class="mt-3 px-2 space-y-1">
                        <a v-for="link in profileLinks"
                           href="#"
                           class="block px-3 py-2 rounded-md text-base font-medium text-gray-400 hover:text-white hover:bg-gray-700">
                            {{ link.displayName }}
                        </a>
                    </div>
                </div>
            </div>
        </nav>


        <slot></slot>
    </div>
</template>

<script>
    import MenuIcon from "@/Icons/MenuIcon";
    import XIcon from "@/Icons/XIcon";
    import MenuLinks from "@/Layouts/Partials/MenuLinks";
    import AppLogo from "@/Icons/AppLogo";
    import SearchIcon from "@/Icons/SearchIcon";
    import BellIcon from "@/Icons/BellIcon";
    import ProfileDropdownComponent from "@/Layouts/Partials/ProfileDropdownComponent";
    import AppLogoCompact from "@/Icons/AppLogoCompact";

    export default {
        data() {
            return {
                isOpen: false,
                profileLinks: [
                    {
                        displayName: 'Your Profile'
                    },
                    {
                        displayName: 'Settings'
                    },
                    {
                        displayName: 'Sign out'
                    }
                ]
            }
        },

        components: {
            AppLogoCompact,
            ProfileDropdownComponent,
            BellIcon,
            SearchIcon,
            AppLogo,
            MenuLinks,
            XIcon,
            MenuIcon
        },
    }
</script>
