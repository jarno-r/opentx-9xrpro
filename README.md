## OpenTX 2.3 fork for various fixes for Turnigy 9XR Pro

### Fixed issues

* 4-in-1 multimodule menu not working. [#8946](https://github.com/opentx/opentx/pull/8946)
* 4-in-1 multimodule telemetry not working due to missing inversion. [#8954](https://github.com/opentx/opentx/issues/8954).
* FlySky AFHDS2A frequent "telemetry lost" & "telemetry recovered" warnings on Moblite7 when disarmed. (Too small `TELEMETRY_TIMEOUT10ms`.)
* RTC not working. [#7421](https://github.com/opentx/opentx/issues/7421)

### To be fixed issues

* Audio playback often fails and requires restart to recover.
  * There might be some issues with SD card reading.
  * Alternatively, opentx crashes.
* Occasional crash when changing models. [#7772](https://github.com/opentx/opentx/issues/7772).
* Sometimes the radio starts up without splash screen. Then SD card doesn not work.
* Radio hangs on startup splash screen occasionally.
* Radio hangs on shutdown splash screen occasionally.
* Companion shuts down when closing a model editor window. (Not 9XR Pro specific.)
* Companion messes up input channel sources.
  * Input sources change to ???. Switches change to P1, P2 or P3. MAX might change to CYC1.

*NOTE:* On an unexpected shutdown, sdInit() is not called. Then audio does not work. This is expected behaviour. (Although maybe it should fallback to tone generator?).

### Building
````
cmake -DDISABLE_COMPANION=ON -DSIMU_TARGET=OFF -DPCB=9XRPRO -DDEFAULT_MODE=2 -DGVARS=YES -DPPM_UNIT=US -DHELI=NO -DLUA=NO -DCMAKE_BUILD_TYPE=Release ../ && make -j`nproc` firmware
````
