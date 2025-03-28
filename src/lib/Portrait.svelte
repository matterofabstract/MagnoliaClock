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
    <img src="/GELogoMark.png" alt="Top" class="absolute top-[52px] left-[18px] w-[150px] aspect-auto" />

    <div class="absolute bottom-[11px] left-[17px] flex flex-col justify-around items-center gap-0.5">
      <div class="flex items-center justify-center p-1" style="background: #2c170a; box-shadow: inset 1px 0 3px 0 rgba(0,0,0,0.20); border-radius: 5px;">
        <button class="w-[160px] h-[68px]"  style="background-image: linear-gradient(178deg, #131210 0%, #151312 40%, #100F0E 100%); border: 0 solid rgba(4,4,4,0.49); border-radius: 6px;" aria-label="Snooz"></button>
      </div>
      <p class="text-white text-[9px] opacity-50 font-semibold uppercase">Snooz</p>
    </div>
  </div>

  <div class="relative w-full h-[194px] flex flex-col items-start justify-start pt-5.5">

    <!-- Panel background -->
    <div class="absolute top-0 left-0 w-full h-full z-0">
      <svg width="100%" height="100%" viewBox="0 0 376 186" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
          <defs>
              <linearGradient x1="50%" y1="62.3008%" x2="37.8677083%" y2="40.0226129%" id="linearGradient-1">
                  <stop stop-color="#110E0Cad" offset="0%"></stop>
                  <stop stop-color="#1C1C1Cad" offset="100%"></stop>
              </linearGradient>
              <radialGradient cx="71.4365858%" cy="10.2234543%" fx="71.4365858%" fy="10.2234543%" r="170.673689%" gradientTransform="translate(0.714366,0.102235),scale(0.494681,1.000000),rotate(72.453980),scale(1.000000,3.317522),translate(-0.714366,-0.102235)" id="radialGradient-2">
                  <stop stop-color="#FFFFFFad" stop-opacity="0.934495192" offset="0%"></stop>
                  <stop stop-color="#000000ad" offset="100%"></stop>
              </radialGradient>
          </defs>
          <g id="GE-Alarm-Block-(iPhone-App)" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
              <g id="Home" transform="translate(0.000000, -239.000000)" fill-rule="nonzero">
                  <g id="Silver-Frame" transform="translate(0.000000, 239.000000)">
                      <rect id="Rectangle-2-Copy-3" fill="url(#linearGradient-1)" x="0" y="0" width="375" height="186"></rect>
                      <path d="M376,0 L376,186 L0,186 L0,0 L376,0 Z M350.503882,5.33971292 L25.4955804,5.33971292 C18.5386329,5.33971292 12.8147354,10.8167289 12.5082054,17.7669201 L12.5082054,17.7669201 L5.92259801,167.087494 C5.91418234,167.278309 5.90997297,167.469287 5.90997297,167.660287 C5.90997297,174.839989 11.7302712,180.660287 18.909973,180.660287 L18.909973,180.660287 L357.08949,180.660287 C357.28049,180.660287 357.471468,180.656078 357.662283,180.647662 C364.835012,180.331317 370.39321,174.260223 370.076865,167.087494 L370.076865,167.087494 L363.491257,17.7669201 C363.184727,10.8167289 357.46083,5.33971292 350.503882,5.33971292 L350.503882,5.33971292 Z" id="Combined-Shape" fill="url(#radialGradient-2)"></path>
                  </g>
              </g>
          </g>
      </svg>
    </div>

    <!-- Main Display -->
    <div class="flex justify-center items-start w-full h-[83px] z-10">

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
   <div class="max-w-[calc(100%-50px)] w-full mx-auto mt-0.5 z-10">
     <div class="min-h-[68px] rounded w-full bg-[#453D3930] flex flex-col items-start justify-center text-white text-xs pl-4 pr-2">
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
        <div class="px-3 py-1 bg-[#121212] rounded w-full">
          <div class="relative px-3 py-1 bg-[#191919] rounded">
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


