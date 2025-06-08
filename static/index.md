# About

BLE Scale Display for LilyGo T5 V2.3.1

Can be found here 
https://tinyurl.com/eInk-Diplay

# Installation

You can use the button below to install the pre-built firmware directly to your device via USB from the browser.

## Set your BLE server MAC address

<label for="ble_mac"><strong>BLE Server MAC address</strong></label><br>
<input  id="ble_mac"
        type="text"
        placeholder="E8:06:90:95:98:69"
        pattern="([0-9a-fA-F]{2}:){5}[0-9a-fA-F]{2}"
        style="width:200px; margin-top:0.25rem;"><br><br>

<button onclick="generateYaml()">Copy substitution block</button>

<pre id="yaml_out"
     style="background:#111; color:#0f0; padding:1rem; border-radius:6px;"></pre>

<script>
function generateYaml() {
  const mac = document.getElementById('ble_mac').value.trim();
  if (!/^([0-9A-Fa-f]{2}:){5}[0-9A-Fa-f]{2}$/.test(mac)) {
    alert("Please enter a valid MAC address (AA:BB:CC:DD:EE:FF)");
    return;
  }
  const yaml = `
substitutions:
  ble_server_mac: ${mac}
`;
  document.getElementById('yaml_out').textContent = yaml.trim();
  navigator.clipboard?.writeText(yaml.trim());
}
</script>

<esp-web-install-button manifest="firmware/dak-keg-display.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"></script>
