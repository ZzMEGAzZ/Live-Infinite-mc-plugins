# Live Infinite MC Plugins

Plugin manifest + built jars for the Live Infinite desktop app's Minecraft
plugin marketplace. Polled at runtime via `marketplace.ts`'s
`DEFAULT_MANIFEST_URL`:
`https://raw.githubusercontent.com/ZzMEGAzZ/Live-Infinite-mc-plugins/main/manifest.json`

`manifest.json` is a `PluginManifestEntry[]` — see
`shared/src/types/minecraftServer.ts` in the `Live-Infinite` repo for the
exact schema. Each version's `file` is resolved relative to `manifest.json`'s
own directory (this repo's root), and its `sha256` is verified by the app
before install.

Plugin source lives in the private
[`Live-Infinite-Minecraft`](https://github.com/ZzMEGAzZ/Live-Infinite-Minecraft)
repo. There's no CI here yet — cutting a new version means: bump the plugin's
own version, `./gradlew build`, `sha256sum` the jar, then update this repo's
`manifest.json` and drop in the new jar by hand.
