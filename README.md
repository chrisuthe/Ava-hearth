# Hearth fork

This is [chrisuthe/Ava-hearth](https://github.com/chrisuthe/Ava-hearth), a fork of
[brownard/Ava](https://github.com/brownard/Ava) that [Hearth](https://github.com/chrisuthe/Hearth-Home)
builds into its Android app. Ava is licensed under Apache-2.0 (see `LICENSE.md`), and so is this fork.
The `hearth` branch carries our changes; `master` tracks upstream. `UPSTREAM_PIN` records the upstream
commit the branch is based on.

## Changes in this fork

Apache-2.0 §4(b) asks for a notice on changed files. In commit `938b4c6` we:

- **Moved** the device code (`esphome`, `server`, `wakewords`, `nsd`, three helpers in `settings` and
  `utils`), its tests and its assets from `:app` into a new `:satellite` library module. Package names
  and file contents are unchanged; each file listed below moved without edits.
- **Added** `satellite/build.gradle.kts`, `satellite/consumer-rules.pro`, `satellite/.gitignore`,
  `satellite/src/main/AndroidManifest.xml` and `UPSTREAM_PIN`.
- **Changed** `settings.gradle.kts` and `app/build.gradle.kts` to include the module and depend on it,
  and `.github/workflows/test.yml` to run its tests.

<details>
<summary>The 80 moved files</summary>

| From | To |
|---|---|
| `app/src/androidTest/assets/hey_jarvis.json` | `satellite/src/androidTest/assets/hey_jarvis.json` |
| `app/src/androidTest/assets/hey_jarvis.tflite` | `satellite/src/androidTest/assets/hey_jarvis.tflite` |
| `app/src/androidTest/assets/wakeWords/computer.json` | `satellite/src/androidTest/assets/wakeWords/computer.json` |
| `app/src/androidTest/assets/wakeWords/computer.tflite` | `satellite/src/androidTest/assets/wakeWords/computer.tflite` |
| `app/src/androidTest/assets/wakeWords/computer.wav` | `satellite/src/androidTest/assets/wakeWords/computer.wav` |
| `app/src/androidTest/assets/wakeWords/okay_nabu.json` | `satellite/src/androidTest/assets/wakeWords/okay_nabu.json` |
| `app/src/androidTest/assets/wakeWords/okay_nabu.tflite` | `satellite/src/androidTest/assets/wakeWords/okay_nabu.tflite` |
| `app/src/androidTest/assets/wakeWords/okay_nabu.wav` | `satellite/src/androidTest/assets/wakeWords/okay_nabu.wav` |
| `app/src/androidTest/java/com/example/ava/AssetWakeWordProviderTest.kt` | `satellite/src/androidTest/java/com/example/ava/AssetWakeWordProviderTest.kt` |
| `app/src/androidTest/java/com/example/ava/MicroWakeWordTest.kt` | `satellite/src/androidTest/java/com/example/ava/MicroWakeWordTest.kt` |
| `app/src/main/assets/sounds/LICENSE.md` | `satellite/src/main/assets/sounds/LICENSE.md` |
| `app/src/main/assets/sounds/error.flac` | `satellite/src/main/assets/sounds/error.flac` |
| `app/src/main/assets/sounds/timer_finished.flac` | `satellite/src/main/assets/sounds/timer_finished.flac` |
| `app/src/main/assets/sounds/wake_word_triggered.flac` | `satellite/src/main/assets/sounds/wake_word_triggered.flac` |
| `app/src/main/assets/stopWords/stop.json` | `satellite/src/main/assets/stopWords/stop.json` |
| `app/src/main/assets/stopWords/stop.tflite` | `satellite/src/main/assets/stopWords/stop.tflite` |
| `app/src/main/assets/wakeWords/alexa.json` | `satellite/src/main/assets/wakeWords/alexa.json` |
| `app/src/main/assets/wakeWords/alexa.tflite` | `satellite/src/main/assets/wakeWords/alexa.tflite` |
| `app/src/main/assets/wakeWords/choo_choo_homie.json` | `satellite/src/main/assets/wakeWords/choo_choo_homie.json` |
| `app/src/main/assets/wakeWords/choo_choo_homie.tflite` | `satellite/src/main/assets/wakeWords/choo_choo_homie.tflite` |
| `app/src/main/assets/wakeWords/hey_home_assistant.json` | `satellite/src/main/assets/wakeWords/hey_home_assistant.json` |
| `app/src/main/assets/wakeWords/hey_home_assistant.tflite` | `satellite/src/main/assets/wakeWords/hey_home_assistant.tflite` |
| `app/src/main/assets/wakeWords/hey_jarvis.json` | `satellite/src/main/assets/wakeWords/hey_jarvis.json` |
| `app/src/main/assets/wakeWords/hey_jarvis.tflite` | `satellite/src/main/assets/wakeWords/hey_jarvis.tflite` |
| `app/src/main/assets/wakeWords/hey_luna.json` | `satellite/src/main/assets/wakeWords/hey_luna.json` |
| `app/src/main/assets/wakeWords/hey_luna.tflite` | `satellite/src/main/assets/wakeWords/hey_luna.tflite` |
| `app/src/main/assets/wakeWords/hey_mycroft.json` | `satellite/src/main/assets/wakeWords/hey_mycroft.json` |
| `app/src/main/assets/wakeWords/hey_mycroft.tflite` | `satellite/src/main/assets/wakeWords/hey_mycroft.tflite` |
| `app/src/main/assets/wakeWords/hey_peppa_pig.json` | `satellite/src/main/assets/wakeWords/hey_peppa_pig.json` |
| `app/src/main/assets/wakeWords/hey_peppa_pig.tflite` | `satellite/src/main/assets/wakeWords/hey_peppa_pig.tflite` |
| `app/src/main/assets/wakeWords/okay_computer.json` | `satellite/src/main/assets/wakeWords/okay_computer.json` |
| `app/src/main/assets/wakeWords/okay_computer.tflite` | `satellite/src/main/assets/wakeWords/okay_computer.tflite` |
| `app/src/main/assets/wakeWords/okay_nabu.json` | `satellite/src/main/assets/wakeWords/okay_nabu.json` |
| `app/src/main/assets/wakeWords/okay_nabu.tflite` | `satellite/src/main/assets/wakeWords/okay_nabu.tflite` |
| `app/src/main/java/com/example/ava/esphome/EspHomeDevice.kt` | `satellite/src/main/java/com/example/ava/esphome/EspHomeDevice.kt` |
| `app/src/main/java/com/example/ava/esphome/android/logger/TimberLogger.kt` | `satellite/src/main/java/com/example/ava/esphome/android/logger/TimberLogger.kt` |
| `app/src/main/java/com/example/ava/esphome/android/mediaplayer/AudioFocusRegistration.kt` | `satellite/src/main/java/com/example/ava/esphome/android/mediaplayer/AudioFocusRegistration.kt` |
| `app/src/main/java/com/example/ava/esphome/android/mediaplayer/Media3MediaPlayer.kt` | `satellite/src/main/java/com/example/ava/esphome/android/mediaplayer/Media3MediaPlayer.kt` |
| `app/src/main/java/com/example/ava/esphome/android/microphone/AudioRecordMicrophone.kt` | `satellite/src/main/java/com/example/ava/esphome/android/microphone/AudioRecordMicrophone.kt` |
| `app/src/main/java/com/example/ava/esphome/android/wakeword/MicroWakeWord.kt` | `satellite/src/main/java/com/example/ava/esphome/android/wakeword/MicroWakeWord.kt` |
| `app/src/main/java/com/example/ava/esphome/entities/Entity.kt` | `satellite/src/main/java/com/example/ava/esphome/entities/Entity.kt` |
| `app/src/main/java/com/example/ava/esphome/entities/MediaPlayerEntity.kt` | `satellite/src/main/java/com/example/ava/esphome/entities/MediaPlayerEntity.kt` |
| `app/src/main/java/com/example/ava/esphome/entities/SwitchEntity.kt` | `satellite/src/main/java/com/example/ava/esphome/entities/SwitchEntity.kt` |
| `app/src/main/java/com/example/ava/esphome/logger/Logger.kt` | `satellite/src/main/java/com/example/ava/esphome/logger/Logger.kt` |
| `app/src/main/java/com/example/ava/esphome/mediaplayer/MediaPlayer.kt` | `satellite/src/main/java/com/example/ava/esphome/mediaplayer/MediaPlayer.kt` |
| `app/src/main/java/com/example/ava/esphome/microphone/Microphone.kt` | `satellite/src/main/java/com/example/ava/esphome/microphone/Microphone.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/Announcement.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/Announcement.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/VoiceAssistant.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/VoiceAssistant.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/VoiceInput.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/VoiceInput.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/VoiceOutput.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/VoiceOutput.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/VoicePipeline.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/VoicePipeline.kt` |
| `app/src/main/java/com/example/ava/esphome/voiceassistant/VoiceTimer.kt` | `satellite/src/main/java/com/example/ava/esphome/voiceassistant/VoiceTimer.kt` |
| `app/src/main/java/com/example/ava/esphome/wakeword/WakeWord.kt` | `satellite/src/main/java/com/example/ava/esphome/wakeword/WakeWord.kt` |
| `app/src/main/java/com/example/ava/nsd/NsdRegistration.kt` | `satellite/src/main/java/com/example/ava/nsd/NsdRegistration.kt` |
| `app/src/main/java/com/example/ava/nsd/VoiceSatelliteNsd.kt` | `satellite/src/main/java/com/example/ava/nsd/VoiceSatelliteNsd.kt` |
| `app/src/main/java/com/example/ava/server/ClientConnection.kt` | `satellite/src/main/java/com/example/ava/server/ClientConnection.kt` |
| `app/src/main/java/com/example/ava/server/Server.kt` | `satellite/src/main/java/com/example/ava/server/Server.kt` |
| `app/src/main/java/com/example/ava/settings/SettingState.kt` | `satellite/src/main/java/com/example/ava/settings/SettingState.kt` |
| `app/src/main/java/com/example/ava/utils/AsyncUtils.kt` | `satellite/src/main/java/com/example/ava/utils/AsyncUtils.kt` |
| `app/src/main/java/com/example/ava/utils/BufferUtils.kt` | `satellite/src/main/java/com/example/ava/utils/BufferUtils.kt` |
| `app/src/main/java/com/example/ava/wakewords/microwakeword/MicroWakeWordDetector.kt` | `satellite/src/main/java/com/example/ava/wakewords/microwakeword/MicroWakeWordDetector.kt` |
| `app/src/main/java/com/example/ava/wakewords/microwakeword/MicroWakeWordModel.kt` | `satellite/src/main/java/com/example/ava/wakewords/microwakeword/MicroWakeWordModel.kt` |
| `app/src/main/java/com/example/ava/wakewords/microwakeword/TensorBuffer.kt` | `satellite/src/main/java/com/example/ava/wakewords/microwakeword/TensorBuffer.kt` |
| `app/src/main/java/com/example/ava/wakewords/models/WakeWord.kt` | `satellite/src/main/java/com/example/ava/wakewords/models/WakeWord.kt` |
| `app/src/main/java/com/example/ava/wakewords/providers/AssetWakeWordProvider.kt` | `satellite/src/main/java/com/example/ava/wakewords/providers/AssetWakeWordProvider.kt` |
| `app/src/main/java/com/example/ava/wakewords/providers/DocumentTreeWakeWordProvider.kt` | `satellite/src/main/java/com/example/ava/wakewords/providers/DocumentTreeWakeWordProvider.kt` |
| `app/src/main/java/com/example/ava/wakewords/providers/WakeWordProvider.kt` | `satellite/src/main/java/com/example/ava/wakewords/providers/WakeWordProvider.kt` |
| `app/src/test/java/com/example/ava/AnnouncementTest.kt` | `satellite/src/test/java/com/example/ava/AnnouncementTest.kt` |
| `app/src/test/java/com/example/ava/VoiceAssistantTest.kt` | `satellite/src/test/java/com/example/ava/VoiceAssistantTest.kt` |
| `app/src/test/java/com/example/ava/VoiceAssistantTimerTest.kt` | `satellite/src/test/java/com/example/ava/VoiceAssistantTimerTest.kt` |
| `app/src/test/java/com/example/ava/VoiceInputTest.kt` | `satellite/src/test/java/com/example/ava/VoiceInputTest.kt` |
| `app/src/test/java/com/example/ava/VoiceOutputTest.kt` | `satellite/src/test/java/com/example/ava/VoiceOutputTest.kt` |
| `app/src/test/java/com/example/ava/VoicePipelineTest.kt` | `satellite/src/test/java/com/example/ava/VoicePipelineTest.kt` |
| `app/src/test/java/com/example/ava/VoiceTimerTest.kt` | `satellite/src/test/java/com/example/ava/VoiceTimerTest.kt` |
| `app/src/test/java/com/example/ava/stubs/StubMediaPlayer.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubMediaPlayer.kt` |
| `app/src/test/java/com/example/ava/stubs/StubMicrophone.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubMicrophone.kt` |
| `app/src/test/java/com/example/ava/stubs/StubSetting.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubSetting.kt` |
| `app/src/test/java/com/example/ava/stubs/StubVoiceInput.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubVoiceInput.kt` |
| `app/src/test/java/com/example/ava/stubs/StubVoiceOutput.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubVoiceOutput.kt` |
| `app/src/test/java/com/example/ava/stubs/StubWakeWord.kt` | `satellite/src/testShared/java/com/example/ava/stubs/StubWakeWord.kt` |

</details>

The upstream README follows.

---

# Android Voice Assistant (Ava)

Experimental Android voice assistant for [Home Assistant][homeassistant] that uses the [ESPHome][esphome] protocol.

Intended for turning your existing Android wall panel or similar into a local voice assistant for controlling your smart home using Home Assistant.

⚠️**Warning: This app is intended for 'static' local devices like a wall panel on a trusted network, it is not suitable for your mobile device (though it probably will work) for the following reasons**⚠️
- It exposes a port to allow incoming connections from Home Assistant with no authentication whatsoever (the device is the server in the ESPHome API) so shouldn't be used on any untrusted networks. Additionally the device needs to be reachable from Home Assistant for the app to function, which probably means the device will need to remain on the local network.
- It is constantly using the microphone to listen for the wake word, which is not only a privacy issue but also a battery drain. Android does not allow non-system apps to listen 'passively' like the built in assistants.

Requires Android 8 or above.

[![paypal](https://www.paypalobjects.com/en_GB/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate/?business=EU5MC92FG3JF6&no_recurring=0&currency_code=GBP)

# Implemented
- Local wake word detection using up to two microWakeWord models
- Stop word detection
- Custom wake word support
- Voice commands
- Announcements and conversations
- Media player
- Microphone mute switch
- Wake/preannounce sounds
- Timers
- [Tasker integration](docs/TASKER.md)
- [Audio processing](docs/AUDIO_PROCESSING.md)

# Todo
- Improved Assist feedback on screen
- Display media playback status on screen

# Setup
- Install and run the app
- Optionally change the satellite name and port settings
- Start the satellite service, it will continue to run in the background until manually stopped.
- In Home Assistant:
  - Add or open the ESPHome integration
  - The satellite should be auto-detected in most cases, if not, manually add the satellite using the device's IP address and configured port (Default: 6053)
  - Complete the voice assistant setup wizard
 
# App Settings
Once connected, the satellite is fully configurable from within Home Assistant as a ESPHome voice satellite and media player, however some settings can also be changed from within the app.

- Name: The display name of the satellite. Requires service restart
- Port: The port to listen on. Requires service restart
- Autostart service: Whether to automatically start the satellite service on application start
- Wake word 1 and Wake word 2: The wake words to use (second is optional). Note that changing this in the app does immediately change the wake word, however currently the change is not reflected in Home Assistant. It is recommended to change the wake word from Home Assistant to ensure the configuration remains in sync.
- Custom wake words: Specify a directory on the device containing custom wake word models
- Enable wake sound: Whether to play a sound when the satellite is woken by a wake word
- Custom timer sound: Specify an audio file to play instead of the default one
- Repeat timer sound: By default, the timer sound is repeated until stopped by the user

# Logs

Logs for the app can be sent to and displayed in Home Assistant's logs to help troubleshooting. See here for instructions on how to enable - [Obtaining logs from the device](https://www.home-assistant.io/integrations/esphome/#obtaining-logs-from-the-device)

# Custom wake word models
The app includes a default [set of wake words](https://github.com/brownard/Ava/tree/master/app/src/main/assets/wakeWords), however you can also specify a directory containing custom wake words supported by microWakeWord.  
Create a directory on your device, copy the wake word model(s) as well as valid json file(s) describing each model ([example](https://github.com/brownard/Ava/blob/master/app/src/main/assets/wakeWords/okay_nabu.json)), a minimum valid example json is:
```
{
  "type": "micro",
  "wake_word": "Custom Wake Word",
  "model": "custom_wakeword.tflite",
  "micro": {
    "probability_cutoff": 0.97,
    "sliding_window_size": 5
  }
}
```
Choose the directory in the 'Custom wake words' setting in the app. The wake word(s) in the directory should now be selectable in the app, however you will need to restart the service in order for the new wake words to show in Home Assistant.  
**If your custom wake words do not appear, double check you have included a valid json file with at least the properties shown above.**

# Development
1. Clone the repo
2. Open in Android Studio

# Debugging on an emulated device
You will need to redirect incoming connections on the server port to the emulated device
1. From a terminal run `telnet localhost 5554` to telnet into the emulator
2. Enter your auth token if required
3. Run `redir add tcp:6053:6053` to add a redirect for the server port (default 6053) to allow incoming connections to be routed to the device

<!-- Links -->
[homeassistant]: https://www.home-assistant.io/
[esphome]: https://esphome.io/
