<script>
     const cake = new URL('./assets/slicecaki.png', import.meta.url).href;
     const hat = new URL('./assets/pasti.png', import.meta.url).href;
     const gift = new URL('./assets/gift3.png', import.meta.url).href;

     let slice = false;
     let asa = false;

     function eat(id) {
         document.getElementById(id).remove()
         slice = true;
     }

     function finish(id) {
         document.getElementById(id).remove()
         asa = true;
     }



</script>


<main class="blur-panel vignette">
     <div id="cake">
          <div id="table">
               <img on:click={()=>{finish("hat")}} id="hat" class="glow image-glow" src="{hat}"/>
               <img on:click={()=>{eat('caake')}} id="caake" class="glow image-glow" src="{cake}"/>
          </div>
          {#if !slice}
               <span id="sub">(click to slice cake)</span>
               <span id="hed">nom nom timw!</span>
               <span id="hedsub">click on the cake (=ω=)</span>

          {:else}
               {#if !asa}
                    <span id="sub">(click to eat cake)</span>
                    <span id="hed">finish it.</span>
                    <span id="hedsub">click on the slice (=ω=)</span>

               {:else}
               <span id="sub">(click to open gift)</span>
               <span id="hed"> O-O </span>
               <span id="hedsub">click on the giftttyay (=ω=)</span>
               <img id="gift" on:click={()=>{setTimeout(() =>{window.location.href='tiyasadi/#/gift'})}} class="glow image-glow" src="{gift}"/>
               {/if}



          {/if}

     </div>
     <div></div>
</main>

<style>
     main{
          width: 100%;
          height: 100%;
     }

     :global(body){
       height: 100vh;
       width: 100%;
       background: conic-gradient(
         #dc57af 90deg,
         #a80f75 90deg 180deg,
         #dc57af 180deg 270deg,
         #a80f75 270deg
       );
       background-repeat: repeat;
       background-size: 80px 80px;
       background-position: 0 0;
       animation-duration: 6s;
       animation-timing-function: linear;
       animation-iteration-count: infinite;
       animation-name: scroll-diag;
     }

     #caake{
          height: 210px;
          width: 170px;
          position: absolute;
          top: 10%;
          left: 10%;
     }


     #hat{
          height: 210px;
          width: 170px;
          position: absolute;
          top: 10%;
          left: 10%;
     }

     #gift{
          width: 180px;
          height: 180px;

          position: absolute;
          top: 15%;
          left: 5;
     }


     #ballon{
          position: absolute;
          height: 140px;
          width: 140px;
          left: -10%;
          top: 2%;
     }
     #ballon2{
          position: absolute;
          height: 140px;
          width: 140px;
          left: 50%;
          top: 7%;
          z-index: -1;
     }

     #star{
          position: absolute;
          height: 140px;
          width: 140px;
          left: -32%;
          top: 5%;
          z-index: -1;
     }

     #cake{
          position: absolute;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          display: flex;
          justify-content: center;
          align-items: center;
          flex-direction: column;

          height: clamp(200px, 41vh, 600px);
          width: clamp(200px, 20vw, 600px)
     }

      #table{
          height: 100%;
          width: 100%;
     }

      #sub{
           font-size: 1.2rem;
           font-weight: bold;
           color: #fff;
           margin-top: 3rem;

           text-align: center;
           text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.5);
      }

      #hed{
           font-size: 2.4rem;
           width: 200vw;
           font-weight: bold;
           margin-top:2rem;

           color:pink;
           text-align: center;
           text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.5);
      }

      #hedsub{
           font-size: 1.2rem;
           width: 200vw;
           font-weight: bold;
           margin-top: 1rem;
           color: lightgray;
           text-align: center;
           text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.5);
      }


      .vignette {
        --vignette-color: rgba(0,0,0,0.3); /* vignette tint (outer) */
        --vignette-inner: rgba(0,0,0,0.0);  /* center tint (usually transparent) */
        --border-radius: 12px;
        --padding: 1rem;

        position: relative;
        overflow: hidden;
        border-radius: var(--border-radius);
      }

      .blur-panel {
           --blur-size: 0.5px;        /* blur radius */
        background: rgba(255,255,255,0.12); /* adjust for light/dark look */
        backdrop-filter: blur(var(--blur-size));
        -webkit-backdrop-filter: blur(var(--blur-size));
        z-index: 2;
      }

      .vignette::before {
        content: "";
        position: absolute;
        inset: 0;
        pointer-events: none;
        background-image: radial-gradient(
          circle at center,
          var(--vignette-inner) 50%,
          var(--vignette-color) 100%
        );
        mix-blend-mode: multiply;
        z-index: 5;
      }

      .vignette > .content {
        position: relative;
        z-index: 10;
        color: #fff;
      }

      /* Base glow variables (tweak per use) */
      .glow {
        --glow-color: white;     /* RGB or CSS color */
        --glow-size: 50px;         /* blur/spread size */
        --glow-intensity: 0.2;    /* alpha multiplier used for subtle shadows */
        --glow-offset-x: 0px;
        --glow-offset-y: 0px;
        --glow-spread: 6px;        /* for box-shadow spread when used */
        transition: box-shadow 180ms ease, filter 180ms ease, transform 180ms ease;
        /* ensure visible overflow if glow exceeds bounds */
        will-change: box-shadow, filter;
      }

      /* OUTER GLOW - works for images and most elements */
      .outer-glow {
        box-shadow:
          var(--glow-offset-x) var(--glow-offset-y) calc(var(--glow-size) / 1.2)
            calc(var(--glow-spread) * 0.2) rgba(0,0,0,0.0), /* base for layering */
          0 0 var(--glow-size) rgba(0,0,0,0.0),
          0 0 calc(var(--glow-size) * 0.75)
            color-mix(in srgb, var(--glow-color) 60%, transparent);
        /* subtle colored halo using filter (optional stronger effect) */
        filter: drop-shadow(0 0 calc(var(--glow-size) * 0.6) rgba(0,0,0,0.0));
      }

      /* IMAGE-SPECIFIC: use filter: drop-shadow for better results on transparent imgs */
      img.glow.image-glow,
      .glow.image-glow {
        /* drop-shadow keeps glow to shape of image instead of the bounding box */
        filter: drop-shadow(0 0 calc(var(--glow-size) * 0.9) color-mix(in srgb, var(--glow-color) 60%, transparent));
        /* a faint outer blur for extra softness */
        box-shadow: 0 0 calc(var(--glow-size) * 0.25) rgba(0,0,0,0.0);
      }

      /* NEON / STRONG COLOR GLOW */
      .neon {
        --glow-size: 28px;
        --glow-intensity: 0.35;
        /* main neon core + layered outer glows */
        text-shadow:
          0 0 2px color-mix(in srgb, var(--glow-color) 90%, #fff 10%),
          0 0 calc(var(--glow-size) * 0.35) color-mix(in srgb, var(--glow-color) 60%, transparent),
          0 0 calc(var(--glow-size) * 0.9) color-mix(in srgb, var(--glow-color) 30%, transparent);
        box-shadow:
          0 0 calc(var(--glow-size) * 0.75) color-mix(in srgb, var(--glow-color) 40%, transparent);
      }

      /* INSET (inner) GLOW for panels/containers */
      .inset-glow {
        /* inner glow simulated with inset box-shadow and an overlay pseudo-element */
        position: relative;
        box-shadow: inset 0 0 calc(var(--glow-size) * 0.6) rgba(0,0,0,0.0);
        overflow: visible;
      }
      .inset-glow::after {
        content: "";
        position: absolute;
        inset: 0;
        pointer-events: none;
        background: radial-gradient(
          circle at center,
          rgba(255,255,255,0.00) 40%,
          color-mix(in srgb, var(--glow-color) calc(10% * var(--glow-intensity)), transparent 0%)
            100%
        );
        mix-blend-mode: screen;
        filter: blur(calc(var(--glow-size) * 0.35));
        z-index: 1;
      }

      /* PULSE / ANIMATED GLOW */
      .pulse {
        --glow-size: 18px;
        animation: glow-pulse 1.6s ease-in-out infinite;
      }
      @keyframes glow-pulse {
        0% {
          box-shadow: 0 0 calc(var(--glow-size) * 0.4) color-mix(in srgb, var(--glow-color) 40%, transparent);
          transform: translateZ(0) scale(1);
          filter: drop-shadow(0 0 calc(var(--glow-size) * 0.55) color-mix(in srgb, var(--glow-color) 35%, transparent));
        }
        50% {
          box-shadow: 0 0 calc(var(--glow-size) * 1.1) color-mix(in srgb, var(--glow-color) 55%, transparent);
          transform: translateZ(0) scale(1.02);
          filter: drop-shadow(0 0 calc(var(--glow-size) * 1.25) color-mix(in srgb, var(--glow-color) 55%, transparent));
        }
        100% {
          box-shadow: 0 0 calc(var(--glow-size) * 0.4) color-mix(in srgb, var(--glow-color) 40%, transparent);
          transform: translateZ(0) scale(1);
        }
      }

      /* Quick presets (optional) */
      .glow--soft {
        --glow-color: rgba(122, 95, 255, 0.9);
        --glow-size: 14px;
        --glow-spread: 4px;
      }
      .glow--warm {
        --glow-color: #ffb86b;
        --glow-size: 20px;
      }
      .glow--cool {
        --glow-color: #7df9ff;
        --glow-size: 22px;
      }

     @keyframes scroll-diag {
       from { background-position: 0 0; }
       to   { background-position: -60px -60px; }
     }
</style>
