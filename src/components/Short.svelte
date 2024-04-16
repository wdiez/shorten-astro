<script>
    //EIFF.SHORT.GY
    //sk_EAAMAkIZA5pyNsO1
    let url = "";
    let urlResult = "";
    let show = false;

    const fetchUrl = async () => {

        const options = {
            method: 'POST',
            headers : {
                accept: 'application/json',
                'content-type': 'application/json',
                Authorization: 'sk_EAAMAkIZA5pyNsO1'
            },
            body: JSON.stringify({originalURL: url, domain: 'eiff.short.gy'})
        };

        const response = await fetch('https://api.short.io/links', options);
        const data = await response.json();
        console.log(data);
        urlResult = data.shortURL;
    }

    const styleInput = "bg-gray-200 appeareance-none border-2 border-gray-200 rounded w-full py-3 px-4 text-gray-700 leading-tight focus:outline-none focus:border-purple-500";
    const buttonStyle ="bg-purple-500 hover:bg-purple-400 text-white font-bold py-2 px-10 rounded"
</script>

<div class="md:flex md:items-center md-6">
    <div class="md:w-1/3">
        <label for="" class="block text-gray-500 font-bolt md:text-right pr-4">URL to shorten</label>
    </div>
    <div class="md:w-1/3">
        <input type="text" placeholder="Example://www.mysite.com" bind:value={url} class={styleInput}/>
    </div>
</div>

<div class="md:flex md:items-center mt-10 justify-center">
    <button type="button" class={buttonStyle} on:click={fetchUrl}>Shorten</button>
</div>

<h1>{urlResult}</h1>
