<script>
  import { onMount } from 'svelte';
  import QRCode from 'qrcode';

  let url = '';
  let qrCodeSrc = '';

  // Function to generate QR code
  const generateQRCode = () => {
    QRCode.toDataURL(url, (err, src) => {
      if (err) {
        console.error(err);
        return;
      }
      qrCodeSrc = src;
    });
  };
</script>

<style>
  .qr-code {
    width: 150px;
    height: 150px;
  }
</style>

<div>
  <h2>Business Card Generator</h2>
  
  <!-- Input for URL -->
  <label for="url">Enter URL for QR Code:</label>
  <input type="text" id="url" bind:value={url} placeholder="https://example.com" />
  <button on:click={generateQRCode}>Create Business QR Code</button>
  
  <!-- Display QR Code -->
  {#if qrCodeSrc}
    <img class="qr-code" src={qrCodeSrc} alt="QR Code" />
  {/if}
</div>
