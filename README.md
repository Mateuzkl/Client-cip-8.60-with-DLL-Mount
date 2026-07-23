# Tibia 8.60 Client with Extended DLL

An updated CipSoft 8.60 client with:

- DAT/SPR support for frame groups and idle animations
- Mount system
- WASD movement with Chat On/Off
- Smart Walking On/Off
- Updated `ddraw.dll`
- `TibiaExtPatcher` for server deployment

## Client setup

1. Keep `Tibia.exe` and `ddraw.dll` in the same folder.
2. If needed, extract the updated `Tibia.spr` from `Tibia.zip`.
3. Extract `TibiaExtPatcher.rar`.
4. Open the patcher, select `Tibia.exe`, and enter your public IP or DNS name.
5. Click **Patch client + generate server key**.

The patcher:

- configures the server address;
- generates a unique HMAC key;
- updates the DLL integrity signature;
- creates backups of the original EXE and DLL;
- copies the required `config.lua` line to the clipboard.

## Server setup

Paste the generated line into your TFS 1.8 `config.lua`:

```lua
dllCheckHmacKey = "your-generated-64-character-key"
```

Restart the server after changing the key. The same key must be present in the
patched DLL and in the server configuration.

The patcher also creates `SERVER_ONLY_dllCheckHmacKey.lua`. Keep this file on
the server side only. Do not distribute it with the client.

Running the patcher again generates a new key, so remember to update
`config.lua` again.
