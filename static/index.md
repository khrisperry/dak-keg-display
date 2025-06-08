# About

BLE Scale Display for LilyGo T5 V2.3.1

Can be found here 
https://tinyurl.com/eInk-Diplay

# Installation

You can use the button below to install the pre-built firmware directly to your device via USB from the browser.

<label for="ble_mac">BLE Server MAC Address:</label><br>
<input type="text" id="ble_mac" name="ble_mac" placeholder="E8:06:90:95:98:69"><br><br>

<button onclick="generateYaml()">Generate YAML</button>

<pre id="output"></pre>

<script>
  function generateYaml() {
    const mac = document.getElementById('ble_mac').value;
    const yaml = `
substitutions:
  ble_server_mac: ${mac}
  name: dak-keg-display-${mac.replace(/:/g, "").slice(-6)}

packages:
  dskscale.dak-keg-display: github://khrisperry/dak-keg-display/dak-keg-display-esp32.yaml@main
`;
    document.getElementById('output').textContent = yaml;
  }
</script>

<esp-web-install-button manifest="firmware/dak-keg-display.manifest.json"></esp-web-install-button>

<script type="module" src="https://unpkg.com/esp-web-tools@10/dist/web/install-button.js?module"></script>
