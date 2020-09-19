<script>
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

 
  function scannerLoaded() {
    ScanditSDK.configure(
      'ARN/LheRCE7bEFujOh+FQ94sXhF6A9oklVSwHH1sx0lxebmmckmXgtcGQZFFTWSmgwwxSRhrI/6OSHKoFUfyld59BNBJa1s3GFj8x/B4Ef9pRcHoKVa4yQcItVE5T9zj8XzxtE1LDWmyV9ECUlxfth5r4qhyO+J8XC78AE0jDVlFAF3FBaof3k1+7gaTeTeahWtzyWtCwvgNxn7xPSe4hObktmm63U8bFNXrsgqlTFswpSEF/QvPXsZm9QbRnvVPCK6XFkbuTkESmcN2PzJg73v2h6K/hTtdVhyetYVPNEkP2kcq8D6W0cpUM8KYvmyGwuXQC5myljba/bKCWhlgoZptJH8nQDEv8W5lSoS6wxnZyDy5WEfv1XCbUDwaHrVhQMkALPScnmBqqCnmOX+NrAWcNwh9CHZVMjp4Y3fNGBKGSGePkgZdrcFPb2we4MQwYlqwerenN7wwPcmFjPWbOkE782/V5TpWMqP7VBZOnaVuu9INUUOSsP+B++8gYbkAzCFwcXLXzL+m7CwPRPNpx54nmj+sQ7vIGYwnuBGN/vnKgIViORwkmXzg7IU4SzMdfu9H38MHbq9pm9RQCadhJzzRI1Aps6We5zoY/4qQOLCWh3stKfOqk4wae4Dx310GPq5M88fziKncP5XL7pdPFf3auginINpRFykJx5hI2xmwW+LA7eUAWuQNll24v8A0hqd3JDzMMrm88xMBIFsD+nRmzsf/SP8YgUaB7SVeOyPDo+xVziNWNa13eczP6xF7nLOVM9exlBWXQ2gWxro1nhy6T84zYwE2DZ1mgy11ShL4sLHxBn/DKYF/mh3DR7A1oo6RQc8jJ+HozWrTROr31i4e',
      {
        engineLocation: 'https://cdn.jsdelivr.net/npm/scandit-sdk@5.x/build/',
      },
    )
      .then(() => {
        return ScanditSDK.BarcodePicker.create(
          document.getElementById('scandit-barcode-picker'),
          {
            // enable some common symbologies
            scanSettings: new ScanditSDK.ScanSettings({
              enabledSymbologies: ['ean8', 'ean13', 'upca', 'upce'],
            }),
          },
        );
      })
      .then((barcodePicker) => {
        // barcodePicker is ready here, show a message every time a barcode is scanned
        barcodePicker.on('scan', (scanResult) => {
       
        dispatch('message', {
        text: scanResult.barcodes[0].data
          });
        });
      });
  }
</script>

<svelte:head>
  <script
    src="https://cdn.jsdelivr.net/npm/scandit-sdk@5.x"
    on:load={scannerLoaded}>
  </script>
</svelte:head>
<div class="container-fluid">
  <div class="row">
    <div class="col">
      <!-- Start: Basic Card -->
      <div class="card shadow mb-4">
        <div class="card-header py-3">
          <h6 class="text-primary m-0 font-weight-bold">Scanner</h6>
        </div>
        <div id="scandit-barcode-picker" class="card-body" />
      </div>
      <!-- End: Basic Card -->
    </div>
  </div>
</div>
