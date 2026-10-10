STM32 V17.0.0 - GitHub Actions upload package

UPLOAD THESE TWO ITEMS TO THE ROOT OF YOUR GITHUB REPOSITORY:
1. STM32_Firmware.zip
2. .github/workflows/auto_zip_compile.yml  (keep this exact path)

Then open the repository's Actions tab and run:
"Upload ZIP - Build STM32 Firmware"

The workflow also starts automatically when STM32_Firmware.zip or the workflow file is pushed.

What it does:
- Extracts the firmware ZIP into a predictable firmware/ folder.
- Runs the included host regression test script using bash (no chmod required).
- Installs the STMicroelectronics STM32 Arduino core and LiquidCrystal I2C library.
- Locates the .ino file and attempts compilation for STM32F103C8T6 / Blue Pill.
- Uploads .bin/.hex build outputs as an Actions artifact if produced.

Important:
- This package is a GitHub build package, not a claim that compilation has already succeeded.
- The host test script must pass in GitHub Actions, and the STM32 target compile step must also pass.
- A successful compile does not prove real-machine timing or guarantee zero missed pulses; hardware validation is still required.
- The firmware source archive is included unchanged from the supplied V17.0.0 ZIP. This package fixes the GitHub Actions extraction/build workflow; it does not modify machine-control firmware logic.
