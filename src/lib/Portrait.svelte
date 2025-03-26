<script>
  import { onMount, onDestroy } from 'svelte';

  const getFormattedTime = () => {
    const now = new Date();
    const hours = now.getHours();
    const minutes = now.getMinutes().toString().padStart(2, '0');
    const ampm = hours >= 12 ? 'PM' : 'AM';
    const displayHours = hours % 12 || 12;
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

<div class="w-full h-screen min-h-screen flex flex-col items-center justify-start user-select-none overflow-hidden">

  <div class="relative bg-[url('/TOP.png')]  bg-cover bg-center bg-no-repeat w-full h-[250px]">
    <img src="/GELogoMark.png" alt="Top" class="absolute top-[52px] left-[18px] w-[150px]" />

    <div class="absolute bottom-[11px] left-[17px] flex flex-col justify-around items-center gap-0.5">
      <div class="flex items-center justify-center p-1" style="background: #2c170a; box-shadow: inset 1px 0 3px 0 rgba(0,0,0,0.20); border-radius: 5px;">
        <button class="w-[160px] h-[68px]"  style="background-image: linear-gradient(178deg, #131210 0%, #151312 40%, #100F0E 100%); border: 0 solid rgba(4,4,4,0.49); border-radius: 6px;" aria-label="Snooz"></button>
      </div>
      <p class="text-white text-[9px] opacity-50 font-semibold uppercase">Snooz</p>
    </div>
  </div>

  <div class="bg-[url('/PortraitBg.svg')] bg-fit bg-center bg-no-repeat w-full h-[194px] flex flex-col items-start justify-start pt-5.5">

  <div class="flex justify-center items-start w-full h-[83px]">

    <div class="flex italic font-semibold flex-col justify-start py-2 gap-[9px] h-full items-end pr-2 text-[#2c2c2c]" style="font-family:Arial, Helvetica, sans-serif;">
      <div class="text-[13px]">AM</div>
      <div class="text-[11px]">WAKE 1</div>
    </div>

    <div class="flex flex-col flex-grow max-w-[220px]">
      <div class="bg-[#0f0506ad] flex-1 flex items-center justify-between px-3 rounded-lg">
        <div class="flex items-center justify-between flex-col h-full min-h-[35px]">
          <div class="w-2 h-2 rounded-full" style="background-color: {new Date().getHours() >= 12 ? '#1d080b' : '#c90000'};"></div>
          <div class="w-2 h-2 bg-[#1d080b] rounded-full"></div>
        </div>

        <div class="relative flex flex-col items-end justify-center text-4xl mx-2 font-digital font-bold whitespace-nowrap min-h-[60px]">
          <div class="text-[#21080c]">00 00</div>
          <div class="absolute text-[#ff0000]" style="text-shadow: 0 0 10px #ff000021;">{time}</div>
        </div>
        <div class="flex items-center justify-end flex-col h-full min-h-[35px]">
          <div class="w-2 h-2 bg-[#1d080b] rounded-full"></div>
        </div>
      </div>
      <div class="uppercase text text-[#2c2c2c] opacity-80 font-semibold">
        <div class="pt-1 pl-5 text-[10px]">Battery Backup</div>
      </div>
    </div>

    <div class="flex italic font-semibold flex-col items-end justify-start h-full pl-4 pb-2 text-[#2c2c2c]" style="font-family:Arial, Helvetica, sans-serif;">
      <div class="relative top-[-8px]">
        <div class="bg-[url('/GELogoMark.png')] bg-no-repeat w-6 h-6 opacity-20 relative bg-cover"></div>
      </div>
      <div class="text-[11px] relative top-[11px]">WAKE 2</div>
    </div>

  </div>

  <!-- Radio Band -->
   <div class="max-w-[calc(100%-50px)] w-full mx-auto mt-0.5">
     <div class="min-h-[68px] rounded w-full bg-[#453D3945] flex flex-col items-start justify-center text-white text-xs pl-4 pr-2">
      <div class="flex items-end justify-between w-full italic">
        <div class="px-1 bg-[#6f101c] rounded-sm text-[11px]">FM</div>
        <div class="opacity-80">&nbsp;</div>
        <div class="opacity-80">88</div>
        <div class="opacity-80">92</div>
        <div class="opacity-80">96</div>
        <div class="opacity-80">100</div>
        <div class="opacity-80">104</div>
        <div class="opacity-80">108</div>
        <div class="opacity-80 text-[9px]">Mhz</div>
      </div>

      <div class="flex items-center justify-between w-full mt-1">
        <div class="px-3 py-1 bg-[#1b1b1b] rounded w-full">
          <div class="relative px-3 py-1 bg-[#1e1e1e] rounded">
            <div class="absolute left-[calc(50%-10px)] w-[4px] h-[7px] top-0" style="background-image: linear-gradient(180deg, #572114 5%, #A23D26 56%, #AE4027 58%, #A93F27 100%);"></div>
          </div>
        </div>
      </div>

      <div class="flex items-end justify-between w-full mt-1.5 italic">
        <div class="px-1 bg-[#6f101c] rounded-sm text-[11px]">AM</div>
        <div class="opacity-80 text-[9px]">X10</div>
        <div class="opacity-80 text-[11px]">55</div>
        <div class="opacity-80 text-[11px]">65</div>
        <div class="opacity-80 text-[11px]">80</div>
        <div class="opacity-80 text-[11px]">100</div>
        <div class="opacity-80 text-[11px]">130</div>
        <div class="opacity-80 text-[11px]">160</div>
        <div class="opacity-80 text-[9px]">Khz</div>
      </div>

     </div>
   </div>


  </div>


  <!-- Switches -->
   <div class="min-h-[78px] pb-1.5 w-full flex items-center justify-evenly" style="background-image: linear-gradient(180deg, #1C1C1C 20%, #1D1D1D 59%, #121212 100%);">
    <div class="flex flex-col justify-between items-center text-center gap-2">
      <div class="text-white uppercase text-[10px] opacity-80 italic font-semibold">Reverse</div>
      <div class="h-2 w-2 bg-white opacity-75 rounded-full"></div>
      <button
        type="button"
        class="min-w-[57px] h-[16px]"
        style="background-image: linear-gradient(180deg, #A5896B 0%, #A08361 55%, #856345 100%); box-shadow: 0 6px 0 0 rgba(0,0,0,0.20), 0 2px 0 0 #4A321B; border-radius: 2.4px;"
      ></button>
    </div>

    <div class="flex flex-col justify-between items-center text-center gap-2">
      <div class="text-white uppercase text-[10px] opacity-80 italic font-semibold">Reverse</div>
      <div class="h-2 w-2 bg-white opacity-75 rounded-full"></div>
      <button
        type="button"
        class="min-w-[57px] h-[16px]"
        style="background-image: linear-gradient(180deg, #A5896B 0%, #A08361 55%, #856345 100%); box-shadow: 0 6px 0 0 rgba(0,0,0,0.20), 0 2px 0 0 #4A321B; border-radius: 2.4px;"
      ></button>
    </div>

    <div class="flex flex-col justify-between items-center text-center gap-2">
      <div class="text-white uppercase text-[10px] opacity-80 italic font-semibold">Reverse</div>
      <div class="h-2 w-2 bg-white opacity-75 rounded-full"></div>
      <button
        type="button"
        class="min-w-[57px] h-[16px]"
        style="background-image: linear-gradient(180deg, #A5896B 0%, #A08361 55%, #856345 100%); box-shadow: 0 6px 0 0 rgba(0,0,0,0.20), 0 2px 0 0 #4A321B; border-radius: 2.4px;"
      ></button>
    </div>

    <div class="flex flex-col justify-between items-center text-center gap-2">
      <div class="text-white uppercase text-[10px] opacity-80 italic font-semibold">Reverse</div>
      <div class="h-2 w-2 bg-white opacity-75 rounded-full"></div>
      <button
        type="button"
        class="min-w-[57px] h-[16px]"
        style="background-image: linear-gradient(180deg, #A5896B 0%, #A08361 55%, #856345 100%); box-shadow: 0 6px 0 0 rgba(0,0,0,0.20), 0 2px 0 0 #4A321B; border-radius: 2.4px;"
      >
        <div class="flex items-center justify-evenly">
          <div class="h-[13.6px] w-[5.6px]" style="background: rgba(118,92,65,0.64); box-shadow: inset 0 1px 2px 0 rgba(0,0,0,0.47);"></div>
          <div class="h-[13.6px] w-[5.6px]" style="background: rgba(118,92,65,0.64); box-shadow: inset 0 1px 2px 0 rgba(0,0,0,0.47);"></div>
          <div class="h-[13.6px] w-[5.6px]" style="background: rgba(118,92,65,0.64); box-shadow: inset 0 1px 2px 0 rgba(0,0,0,0.47);"></div>
          <div class="h-[13.6px] w-[5.6px]" style="background: rgba(118,92,65,0.64); box-shadow: inset 0 1px 2px 0 rgba(0,0,0,0.47);"></div>
          <div class="h-[13.6px] w-[5.6px]" style="background: rgba(118,92,65,0.64); box-shadow: inset 0 1px 2px 0 rgba(0,0,0,0.47);"></div>
        </div>
      </button>
    </div>
   </div>

  <!-- Alarm Setters -->
  <div class="h-[100px] w-full" style="background-image: linear-gradient(179deg, #1C1C1C 50%, #1B1B1B 58%, #121212 100%);">

  </div>

  <!-- Wood Trim -->
  <div class="bg-[url('/TOP.png')] bg-cover bg-[100%_98%] bg-no-repeat w-full h-[20px] rounded-b-lg shadow-xl z-10">
  <div class=" relative top-[3px] w-full h-full bg-gradient-to-b from-[#00000020] to-transparent"></div>
  </div>

  <!-- Tuning Dial -->
  <div class="z-0 relative mt-[-20px] h-[80px] w-full" style="background-image: linear-gradient(180deg, #1A1A1A 33%, #0E0E0E 100%);">

  </div>

  <!-- Bottom panel -->
   <div class="min-h-[100px] flex-grow-1 w-full" style="background-image: linear-gradient(-11deg, #0F0F0F 0%, #171717 94%); border: 0 solid rgba(74,48,30,0.32);"></div>

  <!-- This hides the swipe bar on iOS by understanding it will invert the color below it -->
  <div class="absolute w-full bottom-[-51px] left-0 justify-center items-center flex user-select-none w-full">
    <div class="w-[138px] h-[4px] bg-white rounded-full"></div>
  </div>
</div>


