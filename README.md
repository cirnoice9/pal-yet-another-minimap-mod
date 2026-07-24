Palworld YetAnotherMinimap Mod
---

To work on this mod put all assets to `Content/Mods/YetAnotherMinimap` of your [Palworld Modding Kit](https://github.com/localcc/PalworldModdingKit), then start the modding kit.

## Optional: settings panel language (zh / en)

The blueprint settings UI ships with English labels. This repo includes an **optional UE4SS Lua companion** that rewrites the Minimap Settings panel to match the **game culture**:

| Game language (`KismetInternationalizationLibrary`) | Settings panel |
|---|---|
| `zh*` (简体 / 繁体) | Chinese |
| anything else | English (stock strings, companion is a no-op) |

### Install

Copy into the **active** UE4SS `Mods` directory (the one UE4SS logs as `Loading mods from:` — on many Steam installs that is `Palworld/Mods/NativeMods/UE4SS/Mods`, not only `Pal/Binaries/Win64/ue4ss/Mods`):

```text
YetAnotherMinimapLoc/enabled.txt
YetAnotherMinimapLoc/Scripts/main.lua
```

In `Mods/mods.txt`:

```text
YetAnotherMinimapLoc : 1
```

### Behaviour (short)

- Detects culture once via `GetCurrentLanguage()`.
- Hooks `WBT_MinimapSettings` `BuildSettingsRows` / `Construct` (post) and watches settings-row widgets so Chinese is applied when the panel is built.
- Translates the floating **Minimap Settings** button as well.
- Leaves config **keys** (`SettingKey` / `.modconfig.json`) in English so save/load stays compatible.
- Heavy work is for the settings UI (title/menu flows). It is not meant to replace a native blueprint string-table localization.

### Notes

- This is **runtime UI text rewrite**, not a rebuilt pak. A future blueprint-native localization would be cleaner for zero-flash English→Chinese.
- Third-party C++ “CHS” DLLs aimed at older 0.5.x builds often fail to hook UMG on current UE4SS Experimental; this companion is maintained against current 0.9/0.10-style settings rows.

## Why this is open source

This mod is open source so that if I (SvenBrnn) ever disappear or stop maintaining it, others have everything they need to fork it and keep it alive. It also serves as an open example of how this kind of mod is built, for anyone learning Palworld/UE4SS modding.

## License

This project is licensed under the [MIT License](LICENSE). In short: you're free to use, modify, fork, and continue development of this mod, but the original copyright notice (crediting SvenBrnn as the original author) must be kept in any copy, fork, or derivative work.
