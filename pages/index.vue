<template>
  <!-- mx-auto h-screen max-w-screen-md bg-red-100 flex flex-col justify-center items-center -->
  <div
    class="mx-auto h-screen max-w-screen-md flex flex-col gap-y-4 justify-center items-center"
  >
    <p class="my-40 px-3 text-xl font-medium rounded-full border-2">
      Tendance acquisition utilisateurs
    </p>
    <!-- <DashUsersMonthTrend chartid="linechart3" /> -->
    <!-- <DashUsers chartid="linechart" /> -->
    <div class="my-60">
      <BarChart />
      <LineChart />
      <PieChart />
    </div>
  </div>
</template>

<script setup></script>
