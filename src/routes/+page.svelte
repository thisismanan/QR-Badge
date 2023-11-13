<style>
    * {
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-family: 'Courier New', monospace;
    }
    select, input{
        color: white;
        padding: 0.4rem;
        margin: 0.2rem;
        border-radius: 0.4rem;
        border: solid gray;
        background: #000;
    }
    
    img {
         margin: 0 auto;
    }
    :root{
        background-color: black;
    }
    
</style>


<script>
    import QRCode from 'qrcode'

    let value = ''
    let imageVal = ''
    let selected = 'L'
    let show = false

    function handleInput(value){

        if(value === '' || null) {
            show = false;
            return
        }
        
         QRCode.toDataURL(value, {errorCorrectionLevel: selected})
    .then(url => {
        imageVal = url
        show = true
        console.log(value);
        
    })
    .catch(err => {
        console.error(err)
    })
    }

    function handlePress(){

    }

   
</script>

<h1>Welcome to QR Generator</h1>
<h3>Use this to generate any type of QR</h3>

<div>
    <input bind:value  on:input={() => handleInput(value)}  type="text" name="" id="">
    <select bind:value={selected} id="error">
        <option value='L'>L </option>
        <option value='M'>M </option>
        <option value='Q'>Q </option>
        <option value='H'>H </option>
    </select>
    <br>
    
</div>
<br>


{#if show === true}
    <img src={imageVal} alt="">
    <p>Download this QR by right clicking on it</p>
{/if}