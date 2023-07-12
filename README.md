# ARM8 tests

Magic flags:

In `./src/window-manager/index.tsx`

```ts
app.commandLine.appendSwitch('use-gl', 'egl');
app.commandLine.appendSwitch('no-sandbox');
app.commandLine.appendSwitch('gpu-sandbox-start-early');
app.commandLine.appendSwitch('ignore-gpu-blacklist');
app.commandLine.appendSwitch('ignore-gpu-blocklist');
app.commandLine.appendSwitch('enable-accelerated-video-decode');
```

and

```ts
function createMainWindow() {
  const window = new BrowserWindow({
    webPreferences: {
      // ...
      enableBlinkFeatures: 'VaapiVideoDecoder', // Use the VaapiVideoDecoder
    },
    // ...
  })
  // ...
```

## To build

```bash
npm_config_arch=arm64 npm_config_platform=linux ARM_VERSION=8 yarn install
arc run build -- -l --arm64
```
