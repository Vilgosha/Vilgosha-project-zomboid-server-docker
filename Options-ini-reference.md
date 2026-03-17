# Project Zomboid — `options.ini` Reference

Client-side options stored in `ZomboidConfig/options.ini`. These settings control display, audio, UI, controls, and graphics for the game client (not the server simulation).

Values shown are from the current configuration.

---

## 🖥️ Display

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `version` | `7` | Internal config version. Managed automatically by the game — do not edit manually. |
| `width` | `1280` | Horizontal resolution in pixels. |
| `height` | `720` | Vertical resolution in pixels. |
| `fullScreen` | `false` | Run the game in fullscreen mode. |
| `borderless` | `false` | Run the game in a borderless window (fullscreen window without OS chrome). |
| `frameRate` | `60` | Target frame rate cap when `uncappedFPS=false`. |
| `uncappedFPS` | `false` | Remove the frame rate cap. May cause excessive GPU usage. |
| `vsync` | `false` | Enable vertical sync to eliminate screen tearing. Ties frame rate to monitor refresh rate. |
| `lockCursorToWindow` | `false` | Confine the mouse cursor to the game window while playing. |
| `zoom` | `true` | Enable mouse wheel zoom in/out. |
| `iso_cursor` | `5` | Cursor style index used in isometric view. |
| `showCursorWhileAiming` | `false` | Keep the OS mouse cursor visible while in aiming mode. |

---

## 🎨 Graphics Quality

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `lighting` | `0` | Lighting quality level. `0`=low, higher values increase quality and GPU load. |
| `lightFPS` | `15` | How many times per second dynamic lighting is recalculated. Lower = better performance. |
| `water` | `0` | Water rendering quality. `0`=low/disabled. |
| `puddles` | `0` | Puddle rendering quality. `0`=disabled. |
| `perfSkybox` | `1` | Skybox rendering quality. `1`=enabled. |
| `perfPuddles` | `0` | Performance-mode puddle rendering. `0`=disabled. |
| `bPerfReflections` | `true` | Enable performance-optimized reflections. |
| `fogQuality` | `0` | Fog rendering quality. `0`=lowest. |
| `renderPrecipitation` | `1` | Rain/snow rendering. `0`=off, `1`=on. |
| `renderPrecipIndoors` | `true` | Render precipitation effects when the player is indoors. |
| `doWindSpriteEffects` | `true` | Animate sprites (trees, bushes) in wind. |
| `doDoorSpriteEffects` | `true` | Animate door sprites when opening/closing. |
| `corpseShadows` | `true` | Render shadows under corpses. |
| `3DGroundItem` | `true` | Render items on the ground in 3D rather than as flat sprites. |
| `bloodDecals` | `10` | Maximum number of blood decals rendered in the world at once. |
| `vidMem` | `3` | Video memory budget index. Higher values allow more textures to stay in VRAM. |

---

## 🖼️ Textures

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `textureCompression` | `true` | Compress textures in VRAM to reduce memory usage. May slightly reduce quality. |
| `modelTextureMipmaps` | `false` | Generate mipmaps for model textures. Improves quality at distance but uses more VRAM. |
| `texture2x` | `true` | Use high-resolution (2x) textures when available. |
| `maxTextureSize` | `1` | Maximum texture resolution index for world/environment textures. |
| `maxVehicleTextureSize` | `2` | Maximum texture resolution index for vehicle textures. |
| `simpleClothingTextures` | `1` | Use simplified clothing textures to reduce VRAM usage. `0`=detailed, `1`=simple. |
| `simpleWeaponTextures` | `false` | Use simplified weapon textures. |

---

## 🔊 Audio

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `soundVolume` | `8` | Master sound effects volume. Scale `0`–`10`. |
| `ambientVolume` | `5` | Ambient environmental sound volume (wind, birds, etc.). Scale `0`–`10`. |
| `musicVolume` | `6` | Background music volume. Scale `0`–`10`. |
| `jumpScareVolume` | `10` | Volume of jump scare sound events. Scale `0`–`10`. |
| `vehicleEngineVolume` | `5` | Volume of vehicle engine sounds. Scale `0`–`10`. |
| `musicActionStyle` | `0` | How music transitions during combat. `0`=standard. |
| `musicLibrary` | `1` | Music library/playlist selection. |

---

## 🎙️ Voice Chat

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `voiceEnable` | `true` | Enable proximity voice chat. |
| `voiceMode` | `3` | Voice chat activation mode. `1`=push-to-talk, `2`=always on, `3`=VAD (voice activity detection). |
| `voiceVADMode` | `3` | Voice Activity Detection sensitivity mode. |
| `voiceAGCMode` | `2` | Automatic Gain Control mode — normalizes mic input volume. |
| `voiceVolumeMic` | `10` | Microphone input volume. Scale `0`–`10`. |
| `voiceVolumePlayers` | `5` | Volume of other players' voices. Scale `0`–`10`. |
| `voiceRecordDeviceName` | *(empty)* | Name of the recording device to use. Empty = system default. |

---

## 🌐 Language & Locale

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `language` | `EN` | Game interface language code. |
| `clockFormat` | `1` | Clock display format. `1`=12-hour, `2`=24-hour. |
| `clock24Hour` | `true` | Use 24-hour time format in the in-game clock. |
| `clockSize` | `2` | Size of the on-screen clock widget. |
| `measurementsFormat` | `Metric` | Unit system for measurements. Options: `Metric`, `Imperial`. |
| `celsius` | `false` | Display temperature in Celsius (legacy option). See also `temperatureDisplayCelsius`. |
| `temperatureDisplayCelsius` | `false` | Display temperature in Celsius in the UI. `false` = Fahrenheit. |
| `contentTranslationsEnabled` | `true` | Apply community translations to modded content. |

---

## 🖱️ UI & HUD

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `fontSize` | `1` | General UI font size index. |
| `contextMenuFont` | `Medium` | Font size for right-click context menus. Options: `Small`, `Medium`, `Large`. |
| `inventoryFont` | `Medium` | Font size in inventory panels. Options: `Small`, `Medium`, `Large`. |
| `tooltipFont` | `Small` | Font size for item tooltips. Options: `Small`, `Medium`, `Large`. |
| `inventoryContainerSize` | `1` | Scale of inventory container UI elements. |
| `uiRenderOffscreen` | `true` | Continue rendering UI elements when they are off-screen (reduces pop-in). |
| `uiRenderFPS` | `20` | Frame rate at which the UI is re-rendered. Lower values improve performance. |
| `progressBar` | `true` | Show timed action progress bars on screen. |
| `showYourUsername` | `true` | Display your own username above your character. |
| `showItemModInfo` | `true` | Show mod source information on item tooltips. |
| `showSurvivalGuide` | `true` | Show the in-game survival guide hints. |
| `objHighlightColor` | `0.98,0.56,0.19` | RGB color used to highlight interactable objects (orange). |
| `goodHighlightColor` | `0.0,1.0,0.0` | RGB color for positive item highlights (green). |
| `badHighlightColor` | `1.0,0.0,0.0` | RGB color for negative item highlights (red). |
| `aimOutline` | `2` | Style of outline drawn around targets while aiming. `0`=none. |
| `singleContextMenu` | `false,false,false,false` | Per-slot setting for collapsing context menus into a single action. |
| `searchModeOverlayEffect` | `1` | Visual overlay effect applied when search mode is active. |

---

## 💬 Chat

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `showChatTimestamp` | `false` | Prepend a timestamp to each chat message. |
| `showChatTitle` | `false` | Show player titles (if set) in chat. |
| `chatFontSize` | `medium` | Font size in the chat window. |
| `minChatOpaque` | `1.0` | Minimum opacity of the chat window when not focused. `0.0`=fully transparent. |
| `maxChatOpaque` | `1.0` | Maximum opacity of the chat window when focused. |
| `chatFadeTime` | `0.0` | Seconds before chat messages fade out. `0.0`=never fade. |
| `chatOpaqueOnFocus` | `true` | Make the chat window fully opaque when the player clicks on it. |

---

## 🕹️ Controls & Input

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `toggleToAim` | `false` | Toggle aiming mode on/off with a single key press instead of holding. |
| `toggleToRun` | `false` | Toggle run mode on/off instead of holding the run key. |
| `toggleToSprint` | `true` | Toggle sprint mode on/off with a single key press. |
| `dblTapJogToSprint` | `false` | Double-tap the jog key to start sprinting. |
| `panCameraWhileAiming` | `true` | Allow camera panning while in aiming mode. |
| `panCameraWhileDriving` | `false` | Allow camera panning while driving a vehicle. |
| `cycleContainerKey` | `shift` | Key used to cycle between nearby containers. |
| `shoulderButtonContainerSwitch` | `1` | Gamepad shoulder button behavior for switching containers. |
| `radialMenuKeyToggle` | `true` | Use a toggle key for the radial action menu instead of hold. |
| `reloadRadialInstant` | `false` | Open the reload radial menu instantly without animation. |
| `enableLeftJoystickRadialMenu` | `true` | Allow the left joystick to open the radial menu on gamepad. |
| `autoProneAtk` | `true` | Automatically stand up from prone when attacking. |
| `updateSneakButton` | `true` | Dynamically update the sneak button hint in the UI. |

---

## 🎒 Inventory & Items

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `autoDrink` | `true` | Automatically drink from a container when the thirst action is triggered. |
| `autoWalkContainer` | `false` | Automatically walk toward a container when interacting with it from a distance. |
| `dropItemsOnSquareCenter` | `false` | Drop items at the center of a tile instead of at the player's exact position. |
| `doContainerOutline` | `true` | Draw an outline around containers in the world. |
| `doDoContainerOutline` | `true` | Secondary flag controlling container outline rendering (legacy duplicate). |
| `leaveKeyInIgnition` | `false` | Leave vehicle keys in the ignition when exiting a vehicle. |
| `ignoreProneZombieRange` | `2` | Radius (tiles) within which prone zombies are ignored for targeting/interaction. |

---

## 🧟 Zombie & Combat

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `reloadDifficulty` | `2` | Difficulty of the weapon reload mini-game. Higher = harder. |
| `rackProgress` | `true` | Show a progress indicator when racking (chambering) a firearm. |
| `timedActionGameSpeedReset` | `false` | Reset game speed to normal after a timed action completes. |
| `tieredZombieUpdates` | `true` | Update distant zombies less frequently to improve performance. |

---

## 📷 Zoom

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `autozoom` | *(empty)* | Saved autozoom preference. Managed automatically by the game. |
| `zoomLevels1x` | `50;75;125;150;175;200` | Available zoom level steps (%) when using 1x textures. |
| `zoomLevels2x` | `50;75;125;150;175;200` | Available zoom level steps (%) when using 2x textures. |

---

## 🗂️ Misc / Internal

| Parameter | Your Value | Description |
|-----------|------------|-------------|
| `tutorialDone` | `false` | Whether the in-game tutorial has been completed. Set to `true` to skip it. |
| `vehiclesWarningShow` | `false` | Whether to show the first-time vehicle warning popup. |
| `doneNewSaveFolder` | `true` | Internal flag confirming migration to the new save folder structure. |
| `rosewoodSpawnDone` | `false` | Whether the Rosewood spawn intro has been shown. |
| `riversideDone` | `false` | Whether the Riverside spawn intro has been shown. |
| `showFirstTimeSneakTutorial` | `true` | Show the sneak tutorial hint on first sneak. |
| `showFirstTimeSearchTutorial` | `true` | Show the search mode tutorial hint on first use. |
| `gotNewBelt` | `false` | Internal flag for the new belt slot UI introduction. |
| `termsOfServiceVersion` | `-1` | Version of the Terms of Service the player has accepted. `-1` = not yet accepted. |
| `seenNews` | *(empty)* | Comma-separated list of news item IDs the player has already seen. |

---

> **Note:** `options.ini` is a **client-side** file. It controls how the game looks and feels for the player connecting to the server, not the server simulation itself. Server behavior is configured in `ZomboidConfig/Server/ZomboidEE.ini`.
