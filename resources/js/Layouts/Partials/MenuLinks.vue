<template>
    <inertia-link v-for="link in links"
                  :href="route(link.routeName)"
                  :class="$page.props.currentRouteName === link.routeName
                                        ? 'bg-gray-900 text-white'
                                        : 'text-gray-300 hover:bg-gray-700 hover:text-white'"
                  class="block px-3 py-2 rounded-md text-base font-medium">
        {{ link.displayName }}
    </inertia-link>
</template>

<script>
    export default {
        name: "MenuLinks",

        data() {
            return {
                links: [
                    {
                        displayName: 'Dashboard',
                        routeName: 'dashboard'
                    },
                    {
                        displayName: 'Team',
                        routeName: 'team'
                    }
                ]
            }
        }
    }
</script>

