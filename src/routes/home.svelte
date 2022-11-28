<script lang="ts">
  let name: string;
  let link: string;
  let directLink: string;
  let addAds: boolean = false;
  let lWarning: boolean = false;
  let nWarning: boolean = false;
  let dWarning: boolean = false;
  let services = { service: "voe" };
  let onChangeService: string = "voe";

  const submit = (e: Event) => {
    e.preventDefault();

    if (!name) {
      nWarning = !nWarning;
      setTimeout(() => (nWarning = !nWarning), 5000);
    }

    if (!link) {
      lWarning = !lWarning;
      setTimeout(() => (lWarning = !lWarning), 5000);
    }

    if (!directLink) {
      dWarning = !dWarning;
      setTimeout(() => (dWarning = !dWarning), 5000);
    }
  };
</script>

{addAds}
{name}
{link}

{directLink}

{onChangeService}

<div
  class="relative flex min-h-screen flex-col justify-center overflow-hidden bg-gray-50 py-6 sm:py-12"
>
  <img
    src="https://play.tailwindcss.com/img/beams.jpg"
    alt=""
    class="absolute top-1/2 left-1/2 max-w-none -translate-x-1/2 -translate-y-1/2"
    width="1308"
  />
  <div
    class="relative bg-white px-6 pt-10 pb-8 shadow-xl ring-1 ring-gray-900/5 sm:mx-auto sm:w-2/3 sm:max-w-lg sm:rounded-lg sm:px-10 md:w-2/3"
  >
    <div class="mx-auto max-w-md">
      <div class="my-4">
        <h2 class="font-mono text-xl text-gray-500">
          {nWarning ? "Name - Please fill the fields" : "Name"}
        </h2>
        <input
          bind:value={name}
          class={nWarning
            ? "w-full border-2 p-2 bg-red-300"
            : "w-full border-2 p-2"}
          type="text"
          placeholder="Example"
        />
      </div>

      <div class="my-4">
        <h2 class="font-mono text-xl text-gray-500">Service</h2>
        <select
          bind:value={services.service}
          on:change={() => (onChangeService = services.service)}
          class="w-full py-3 font-mono text-xl text-gray-500"
          name=""
          id=""
        >
          <option value="voe">Voe</option>
          <option value="okru">Okru</option>
          <option value="filemon">Filemoon</option>
          <option value="fastream">Fastream</option>
          <option value="streamtape">Streamtape</option>
        </select>
      </div>

      <div class="my-4">
        <h2 class="font-mono text-xl text-gray-500">
          {lWarning ? "Link - Please fill the fields" : "Link"}
        </h2>
        <input
          bind:value={link}
          class={lWarning
            ? "w-full border-2 p-2 bg-red-300"
            : "w-full border-2 p-2"}
          type="url"
          placeholder="https://example.com"
        />
      </div>

      <div class="my-4 text-center">
        <h2 class="font-mono text-xl text-gray-500">Advertising</h2>
      </div>

      <div class="my-4 flex items-center justify-center space-x-5">
        <h2 class="font-mono text-xl text-gray-500">Add Ads?</h2>
        <input
          class="p-10"
          checked={addAds}
          on:click={() => ((addAds = !addAds), (directLink = ""))}
          type="checkbox"
        />
      </div>

      <div class="my-4">
        {#if addAds && !dWarning}
          <h2 class="font-mono text-xl text-gray-500">Direct Link</h2>
          <input
            bind:value={directLink}
            class="w-full border-2 p-2"
            type="url"
            placeholder="https://ads.advertisements.com"
          />
        {/if}
        {#if addAds && dWarning}
          <h2 class="font-mono text-xl text-gray-500">
            Direct Link - Please fill the fields
          </h2>
          <input
            bind:value={directLink}
            class="w-full border-2 p-2 bg-red-300"
            type="url"
            placeholder="https://ads.advertisements.com"
          />
        {/if}
      </div>
      <button
        on:click={submit}
        class="mt-4 w-full cursor-pointer bg-green-500 py-2 text-center transition-all hover:bg-red-300"
      >
        <h2 class="font-mono text-xl text-white">Submit</h2>
      </button>
    </div>
  </div>
</div>
