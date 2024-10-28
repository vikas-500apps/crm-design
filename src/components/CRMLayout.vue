<template>
    <div class="flex h-screen bg-gray-50 text-gray-800 text-sm">
        <!-- Sidebar -->
        <div class="w-56 bg-gray-50 border-r border-gray-200 flex flex-col">
            <div class="p-3 mb-4">
                <div class="flex items-center space-x-2">
                    <div
                        class="w-8 h-8 bg-purple-600 rounded-lg flex items-center justify-center text-white font-bold text-lg">
                        <FeatherIcon name="filter" class="w-4 h-4" />
                    </div>
                    <div class="flex flex-col">
                        <span class="font-bold text-base mt-2">CRM</span>
                        <span class="text-xs text-gray-500 mt-1">Sagar Bhogayata</span>
                    </div>
                </div>
            </div>
            <nav class="flex-1 overflow-y-auto">
                <div v-for="(item, index) in sidebarItems" :key="index"
                    class="flex items-center space-x-3 px-4 py-2 hover:bg-gray-100 cursor-pointer">
                    <FeatherIcon :name="item.icon" class="w-4 h-4 text-gray-600" />
                    <span>{{ item.label }}</span>
                </div>
                <div
                    class="flex items-center justify-between text-gray-600 hover:bg-gray-100 cursor-pointer rounded p-2">
                    <div class="flex items-center space-x-2">
                        <FeatherIcon name="chevron-down" class="w-4 h-4 ml-2" />
                        <span>Pinned views</span>
                    </div>
                </div>
            </nav>

            <div class="p-3 border-t border-gray-200">
                <div class="flex items-center space-x-2 text-gray-600 hover:bg-gray-100 cursor-pointer rounded p-2">
                    <FeatherIcon name="chevron-left" class="w-4 h-4" />
                    <span>Collapse</span>
                </div>
            </div>
        </div>

        <!-- Main Content -->
        <div class="flex-1 flex flex-col overflow-hidden">
            <header class="flex items-center justify-between px-6 py-4 border-b border-gray-200 bg-white">
                <div class="flex items-center space-x-4">
                    <h1 class="text-xl font-semibold">Leads / Mr. Bhavesh Maheshwari</h1>
                </div>
                <div class="flex items-center space-x-3">
                    <div class="flex items-center bg-gray-100 px-2 py-1 rounded-md">
                        <Avatar size="sm" label="H" class="bg-blue-100 text-blue-800" />
                        <span class="text-black ml-2">Hardevsinh Rathod</span>
                    </div>
                    <div class="flex px-2 py-1 bg-orange-100 text-orange-800 rounded-md text-xs font-medium">
                        <div class="relative">
                            <FeatherIcon name="circle" class="w-3 bg-orange-800 h-3 mr-2 rounded-full" />
                            <span class="absolute top-1 left-1 w-1 h-1 bg-white rounded-full"></span>
                        </div>
                        Contacted
                        <FeatherIcon name="chevron-down" class="w-4 h-4 ml-2" />
                    </div>

                    <Button :variant="'solid'" theme="gray" size="sm" label="Button">Convert to Deal</Button>
                </div>

            </header>

            <main class="flex-1 overflow-x-hidden overflow-y-auto bg-white">
                <div class="flex">
                    <div class="flex-1 p-6">
                        <div class="flex space-x-6 border-b border-gray-200">
                            <button v-for="tab in tabs" :key="tab" class="pb-3 px-1"
                                :class="activeTab === tab ? 'border-b-2 border-black font-medium' : 'text-gray-500 hover:text-gray-700'"
                                @click="setActiveTab(tab)">
                                {{ tab }}
                            </button>
                        </div>
                        <div class="mt-6">
                            <div class="flex justify-between items-center mb-4">
                                <h2 class="text-lg font-semibold">Notes</h2>
                                <Button :variant="'solid'" theme="gray" size="sm" label="Button">
                                    + New Notes
                                </Button>
                            </div>
                            <div
                                class="flex flex-col items-center justify-center h-[725px] border-2 border-dashed rounded-lg">
                                <div class="p-4 rounded-full bg-gray-100">
                                    <FeatherIcon name="file-text" class="w-8 h-8 text-gray-400" />
                                </div>
                                <p class="mt-4 text-base font-medium text-gray-500">No Notes</p>
                                <button class="mt-2 text-sm text-blue-600 hover:underline">
                                    Create Note
                                </button>
                            </div>

                        </div>
                    </div>

                    <!-- Details Panel -->
                    <div class="w-80 border-l border-gray-200 p-6 bg-white">
                        <p class="text-sm font-semibold mt-1 items-center border-b border-gray-300 pb-2">
                            CRM-LEAD-2024-05534
                        </p>
                        <div class="flex justify-between items-start mb-4">
                            <div>
                                <div class="border-b border-gray-300 pb-2 mt-4">
                                    <div class="flex items-center space-x-3">
                                        <Avatar size="xl" label="B" class="bg-blue-100 text-blue-800" />
                                        <h2 class="text-xl font-semibold">Mr. Bhavesh Maheshwari</h2>
                                    </div>
                                    <div class="flex space-x-2 mt-2 ml-10">
                                        <Avatar size="xl" class="bg-blue-100 text-blue-800">
                                            <FeatherIcon name="mail" class="w-4 h-4 text-black" />
                                        </Avatar>
                                        <Avatar size="xl" class="bg-blue-100 text-blue-800">
                                            <FeatherIcon name="link-2" class="w-4 h-4 text-black" />
                                        </Avatar>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div class="space-y-4 mt-6">
                            <div @click="toggleDetails" class="flex justify-between items-center cursor-pointer">
                                <h3 class="font-medium flex items-center space-x-1">
                                    <FeatherIcon name="chevron-down" class="w-4 h-4" />
                                    <span>Details</span>
                                </h3>
                                <FeatherIcon name="edit" class="w-4 h-4 text-black" />
                            </div>
                            <div v-if="showDetails" v-for="(item, index) in detailsData" :key="index"
                                class="flex justify-between text-sm">
                                <span class="text-gray-500">{{ item.label }}</span>
                                <span class="font-medium text-right">{{ item.value }}</span>
                            </div>
                        </div>
                        <div class="mt-6 space-y-4">
                            <div @click="togglePerson" class="flex justify-between items-center cursor-pointer">
                                <h3 class="font-medium flex space-x-1">
                                    <FeatherIcon name="chevron-down" class="w-4 h-4" />
                                    <span>Person</span>
                                </h3>
                                <FeatherIcon name="edit" class="w-4 h-4 text-black" />
                            </div>
                            <div v-if="showPerson" v-for="(item, index) in personData" :key="index"
                                class="flex justify-between text-sm">
                                <span class="text-gray-500">{{ item.label }}</span>
                                <span class="font-medium">{{ item.value }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </main>
        </div>
    </div>
</template>

<script setup>
import { ref, defineProps } from 'vue';
import { Avatar, Button, FeatherIcon } from 'frappe-ui';

const props = defineProps({
    sidebarItems: {
        type: Array,
        default: () => []
    },
    tabs: {
        type: Array,
        default: () => []
    },
    detailsData: {
        type: Array,
        default: () => []
    },
    personData: {
        type: Array,
        default: () => []
    }
});

const activeTab = ref('Notes');
const showDetails = ref(true);
const showPerson = ref(true);

// Set Active tab
const setActiveTab = (tab) => {
    activeTab.value = tab;
};

const toggleDetails = () => {
    showDetails.value = !showDetails.value;
};

const togglePerson = () => {
    showPerson.value = !showPerson.value;
};
</script>
