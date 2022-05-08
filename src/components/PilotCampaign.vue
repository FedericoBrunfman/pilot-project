<template>
  <div class="flex align-center justify-between border-b-2 p-9">
    <div class="flex">
      <h1 class="text-2xl font-semibold">Name of Campaign No.1</h1>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        enable-background="new 0 0 32 32"
        viewBox="0 0 32 32"
        height="16"
        class="mt-2 ml-4"
        fill="gray"
      >
        <path
          d="M12.82373,12.95898l-1.86279,6.21191c-0.1582,0.52832-0.01367,1.10156,0.37646,1.49121c0.28516,0.28516,0.66846,0.43945,1.06055,0.43945c0.14404,0,0.28906-0.02051,0.43066-0.06348l6.2124-1.8623c0.23779-0.07129,0.45459-0.2002,0.62988-0.37598L31.06055,7.41016C31.3418,7.12891,31.5,6.74707,31.5,6.34961s-0.1582-0.7793-0.43945-1.06055l-4.3501-4.34961c-0.58594-0.58594-1.53516-0.58594-2.12109,0L13.2002,12.3291C13.02441,12.50488,12.89551,12.7207,12.82373,12.95898z M15.58887,14.18262L25.6499,4.12109l2.22852,2.22852L17.81738,16.41113l-3.18262,0.9541L15.58887,14.18262z"
        />
        <path
          d="M30,14.5c-0.82861,0-1.5,0.67188-1.5,1.5v10c0,1.37891-1.12158,2.5-2.5,2.5H6c-1.37842,0-2.5-1.12109-2.5-2.5V6c0-1.37891,1.12158-2.5,2.5-2.5h10c0.82861,0,1.5-0.67188,1.5-1.5S16.82861,0.5,16,0.5H6C2.96729,0.5,0.5,2.96777,0.5,6v20c0,3.03223,2.46729,5.5,5.5,5.5h20c3.03271,0,5.5-2.46777,5.5-5.5V16C31.5,15.17188,30.82861,14.5,30,14.5z"
        />
      </svg>
      <div class="flex flex-col justify-center items-center ml-8">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          class="mt-1 ml-10"
          fill="gray"
          viewBox="0 0 512 512"
        >
          <path
            d="M256 48C141.1 48 48 141.1 48 256s93.1 208 208 208 208-93.1 208-208S370.9 48 256 48zm-32.1 281.7c-2.4 2.4-5.8 4.4-8.8 4.4s-6.4-2.1-8.9-4.5l-56-56 17.8-17.8 47.2 47.2L340 177.3l17.5 18.1-133.6 134.3z"
          />
        </svg>
        <span class="text-xs ml-10 text-gray-500">Saved</span>
      </div>
    </div>
    <div class="journey flex items-center">
      <div class="h-3 w-60 bg-gray-300 rounded-full relative">
        <div class="journey-label absolute text-xs font-semibold">
          Journey Editor
        </div>
        <div class="overview-label absolute text-xs font-semibold">
          Overview
        </div>
        <div class="filled h-3 bg-blue-500 rounded-full absolute"></div>
        <div class="pointer h-5 w-5 bg-blue-500 rounded-full absolute"></div>
        <div
          class="pointer-end h-1 w-1 bg-blue-500 rounded-full absolute"
        ></div>
      </div>
    </div>
    <div class="flex align-center">
      <button
        class="text-xs bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded mx-2"
      >
        Show Analitycs
      </button>
      <button
        class="text-xs bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded mx-2"
      >
        Save & Exit
      </button>
      <button
        class="text-xs bg-transparent hover:bg-blue-500 text-blue-700 font-semibold hover:text-white py-2 px-4 border border-blue-500 hover:border-transparent rounded mx-2"
      >
        Start Automation
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "PilotCampaign",
};
</script>

<style lang="css" scoped>
.filled {
  width: 100px;
}
.pointer {
  left: 90px;
  border: 2px solid white;
  bottom: -3px;
}
.pointer-end {
  right: 5px;
  top: 4px;
}
.journey-label {
  bottom: 22px;
  left: 50px;
}
.overview-label {
  bottom: 22px;
  right: -20px;
}
</style>
