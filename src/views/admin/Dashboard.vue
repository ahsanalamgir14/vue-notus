<template>
    <div class="md:pt-32 pb-32 pt-12">
        <div class="px-4 mx-auto w-full pt-12">
            <h3 class="text-color1 font-weight-300 text-3xl">Dashboard</h3>
            <p class="mt-2 text-color1 text-base italic">Your Application is currently being review, you wil be notified if successful</p>
            <div class="flex flex-wrap">
                <div class="sm:w-4/12 mb-12 xl:mb-0 mt-12">
                    <p>Date of Application</p>
                    <p class="date-application">09.09.19</p>
                    <small class="mt-1">4 days since applied</small>
                    <!-- <card-line-chart /> -->
                </div>
                <div class="sm:w-4/12 mb-12 xl:mb-0 mt-12 pl-100">
                    <p>Application Status</p>
                    <p class="status-application">Pending</p>
                    <small class="mt-1">We will get back to you</small>
                    <!-- <card-line-chart /> -->
                </div>
                <div class="w-full md:w-4/12 px-4">
                    <!-- <card-bar-chart /> -->
                </div>
            </div>
            <div class="flex flex-wrap mt-12">
                <div class="md:w-6/12 mb-12 xl:mb-0">
                    <div class="w-80 max-w-md p-4 bg-white border border-gray-200 rounded-lg shadow sm:p-8 dark:bg-gray-800 dark:border-gray-700">
                        <div class="flex items-center justify-between mb-4">
                            <h5 class="text-sm font-bold leading-none text-gray-900 dark:text-white">Updates</h5>
                        </div>
                        <div class="flow-root">
                            <ul role="list" class="divide-y divide-gray-200 dark:divide-gray-700">
                                <li class="py-6 sm:py-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:py-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:py-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:py-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:pt-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:pt-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                                <li class="py-6 sm:pt-5">
                                    <div class="flex items-center space-x-4">
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="md:w-6/12 mb-12 xl:mb-0 pl-30">
                    <div class="w-80 max-w-md p-4 bg-white border border-gray-200 rounded-lg shadow sm:p-8 dark:bg-gray-800 dark:border-gray-700" style="height: 100%">
                        <div class="flex items-center justify-between mb-4">
                            <h5 class="text-sm font-bold leading-none text-gray-900 dark:text-white">Take Assessment</h5>
                        </div>
                        <div class="flex items-center justify-center flex-col h-full">
                            <p class="text-center">We have 4 days left until the next assessment. Watch this space</p>
                            <div class="mt-4">
                                <button type="button" class="btn1">Take Assessment</button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- <div class="w-full xl:w-8/12 mb-12 xl:mb-0 px-4">
                        <card-page-visits />
                    </div>
                    <div class="w-full xl:w-4/12 px-4">
                        <card-social-traffic />
                    </div> -->
            </div>
        </div>
    </div>
</template>

<script>
// import CardLineChart from "@/components/Cards/CardLineChart.vue";
// import CardBarChart from "@/components/Cards/CardBarChart.vue";
// import CardPageVisits from "@/components/Cards/CardPageVisits.vue";
// import CardSocialTraffic from "@/components/Cards/CardSocialTraffic.vue";
export default {
    name: "dashboard-page",
    components: {
        // CardLineChart,
        // CardBarChart,
        // CardPageVisits,
        // CardSocialTraffic,
    },
};
</script>


<style scoped>
.date-application {
    font-weight: 300;
    font-size: 48px;
    align-items: center;
    border-bottom: 3px solid #006DF0;
}

.status-application {
    font-weight: 300;
    font-size: 48px;
    align-items: center;
    border-bottom: 3px solid #F09000;
}

.pl-100 {
    padding-left: 100px;
}

.pl-30 {
    padding-left: 30px;
}
</style>