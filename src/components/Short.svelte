<script>
    //eyg5.short.gy
    //sk_1xs4xFoOYAzTBIKd

  let url = "";
  let urlResult = "";
  let show = false;

  const fetchUrl = async () => {
    const options = {
        method: 'POST',
        headers:{
            accept: 'application/json',
            'content-type': 'application/json',
            authorization: 'Bearer sk_1xs4xFoOYAzTBIKd'
        },
        body: JSON.stringify({
            originalURL: url, domain: 'eyg5.short.gy'
        })
    };

    const response = await fetch('https://api.short.io/api/links', options);
    const data = await response.json();
    console.log(data);
    urlResult = data.link;
    show = true;

  };

  const styleInput =
    "bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500";

  const buttonStyle = "bg-purple-500 hover:bg-purple-700 text-white font-bold py-2 px-10 rounded";  
</script>

<div class="md:flex md:items-center md-6">
  <div class="md:w-1/3">
    <label for="" class="block text-gray-500 font-bold md:text-right mb-1 md:mb-0 pr-4">
        URL to shorten
    </label>
</div>
  <div class="md:w-1/3">
    <input
      type="text"
      placeholder="Ejemplo://www.misitioweb.com"
      bind:value={url}
      class={styleInput}
    />
  </div>
</div>

<div class="md:flex md:items-center mt-10 justify-center">
    <button type="button" class={buttonStyle} on:click={fetchUrl}> Shorten </button>
</div>
<h1>{urlResult}</h1>
