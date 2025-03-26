<script>
  import { onMount, onDestroy } from 'svelte';

  const getFormattedTime = () => {
    const now = new Date();
    const hours = now.getHours();
    const minutes = now.getMinutes().toString().padStart(2, '0');
    const ampm = hours >= 12 ? 'PM' : 'AM';
    const displayHours = hours % 12 || 12; // Convert 0 to 12 for 12 AM
    return `${displayHours}:${minutes}`;
  };

  let time = getFormattedTime();
  let intervalId;

  onMount(() => {
    document.body.style.backgroundColor = 'black';
  });

  onDestroy(() => {
    document.body.style.backgroundColor = '';
    clearInterval(intervalId);
  });

  intervalId = setInterval(() => {
    time = getFormattedTime();
  }, 1000);
</script>

<div class="w-full min-h-screen flex items-center justify-center user-select-none">
  <!-- The centered display -->
  <div class="flex justify-center items-start" style="width: 100%; min-width: 600px; height: 100%; height: 125px;">

    <div class="flex italic font-semibold flex-col items-end justify-between h-full pr-4 py-2 text-[#2c2c2c] opacity-50" style="font-family:Arial, Helvetica, sans-serif;">
      <div class="text-xl">AM</div>
      <div class="text-lg">WAKE 1</div>
    </div>

    <div class="flex flex-col flex-grow max-w-[500px]">
      <div class="bg-[#0f0506] flex-1 flex items-center justify-between px-3 rounded-lg">
        <div class="flex items-center justify-between flex-col h-full min-h-[90px] mt-1.5">
          <div class="w-3 h-3 rounded-full" style="background-color: {new Date().getHours() >= 12 ? '#1d080b' : '#c90000'};"></div>
          <div class="w-3 h-3 bg-[#1d080b] rounded-full"></div>
        </div>
        <div class="relative flex flex-col items-end justify-center text-8xl mx-2 font-digital font-bold whitespace-nowrap min-h-[120px] pt-2">
          <div class=" mb-4 text-[#21080c]">00 00</div>
          <div class="absolute mb-4 text-[#ff0000]" style="text-shadow: 0 0 10px #ff000021;">{time}</div>
        </div>
        <div class="flex items-center justify-end flex-col h-full min-h-[90px] mt-1.5">
          <div class="w-3 h-3 bg-[#1d080b] rounded-full"></div>
        </div>
      </div>
      <div class="uppercase text text-[#2c2c2c] opacity-50 font-semibold">
        <div class="pt-1.5 pl-7">Battery Backup</div>
      </div>
    </div>

    <div class="flex italic font-semibold flex-col items-end justify-between h-full pl-4 pb-2 text-[#2c2c2c] opacity-50" style="font-family:Arial, Helvetica, sans-serif;">
      <div class="relative top-[-10px]">
        <div class="bg-[url('/GELogoMark.png')] bg-no-repeat w-10 h-10 opacity-20 relative bg-cover"></div>
      </div>
      <div class="text-lg">WAKE 2</div>
    </div>

  </div>

  <!-- This hides the swipe bar on iOS by understanding it will invert the color below it -->
  <div class="absolute w-full bottom-[8px] left-0 justify-center items-center flex user-select-none">
    <div class="w-[217px] h-[5px] bg-white rounded-full"></div>
  </div>
</div>
