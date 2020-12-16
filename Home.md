## Installation

1. Download the Release.zip file from https://github.com/yamashi/PerformanceOverhaulCyberpunk/releases/latest 
2. Unzip everything in `<cyberpunk install path>/bin/x64/`
3. You should see Cyberpunk2077.exe and version.dll in this directory, it means you did it correctly.
4. Launch the game!
5. (Optional) To check that everything works you can look at the logs in `<cyberpunk install path>/bin/x64/plugins/cyber_engine_tweaks/cyber_engine_tweaks.log`

## Troubleshoot

### It says "unknown version" and patches fail

Three options:
1. You modified the exe yourself, in which case the mod will not work! You can repair via GOG or Steam to revert your changes.
2. You are using a patch that is not supported (currently only 1.04 is supported for some patches).
3. You used the old version of the mod and still have the old file, delete `bin/x64/Cyberpunk77.exe.plugins/` and reinstall the mod.

### It doesn't create a log, nothing happens!

Install [this](https://aka.ms/vs/16/release/vc_redist.x64.exe)

## Configuration

Boolean options set to `true` means that you enable the patch!

The options are all found in: `<cyberpunk install path>/bin/x64/plugins/cyber_engine_tweaks/config.json`

* **avx**: Some people encounter a crash due to AVX, the mod will detect if you are at risk and will patch if it's the case. `(default: true)`
* **smt**: This fixes a bug with AMD CPUs causing the game to use only half the CPU. `(default: true)`
* **spectre**: Spectre is a hardware security flaw that can leak a process' memory, the mitigation for spectre has a performance impact. The mitigation doesn't make sense for a game, a spectre exploit is very hard to pull off and there is nothing in Cyberpunk's memory that is sensitive. This patch removes part of the mitigation to get back that lost performance. `(default: true)`.
* **virtual_input**: Not performance related, fixes the input so you can use Steam controllers. `(default: true)`
* **memory_pool**: This will override the default memory pool settings, it gives a decent boost of performance for some users and none for others. `(default: true) `
* **unlock_menu**: Unlocks the debug menu, use at your own risk! `(default: false)`
* **cpu_memory_pool_fraction**: This gives the percentage of CPU memory to use, 1.0 being 100%, 0.5 being 50%. `(default: 0.5)`
* **gpu_memory_pool_fraction**: This gives the percentage of GPU memory to use, 1.0 being 100%, 0.5 being 50%. `(default: 1.0)`
* **remove_pedestrians**: Removes most of the pedestrians and traffic from the game. Be careful using this, a save made with this active will NEVER have pedestrians/traffic anymore! `(default: false)`
* **skip_start_menu**: Skips the main menu asking you to press space bar when "Breaching..." `(default: true)`
* **disable_async_compute**: Setting this to true will disable async compute, can increase performance on older hardware `(default: false)`
* **disable_antialiasing**: Setting this to true will disable antialiasing (TAA), can increase performance on older hardware but looks horrible `(default: false)`

## Uninstall

Just delete `<cyberpunk install path>/bin/x64/version.dll` and `<cyberpunk install path>/bin/x64/plugins/`.