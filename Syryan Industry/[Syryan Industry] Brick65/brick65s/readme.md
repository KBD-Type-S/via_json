# 펌웨어 업로드 방법

1. 아래 3가지 방법 중 하나를 통해서 부트로더에 진입합니다.
2. 부트로더에 정상적으로 진입하였다면 새로운 이동식 디스크가 탐지됩니다. 해당 디스크에 펌웨어 파일을 붙혀넣습니다.

## 부트로더에 진입할 수 있는 3가지 방법

**부트매직을 통한 리셋**: ESC(0,0)을 누른 채 USB 플러그를 연결합니다.
**물리적 리셋을 통한 버튼**: `SWD 헤더`의 `RST`과 `GND`를 짧게 두 번 쇼트시키거나, 또는 `BOOT 헤더`를 쇼트시킨 채로 USB 플러그를 연결합니다.
**키코드를 통한 리셋**: 'QK_BOOT'를 매핑한 후 키를 누릅니다.


# How to upload firmware

1. Enter the bootloader using one of the three ways below.
2. If you enter the bootloader properly, a new removable disk will be detected. Paste the firmware file into that disk.

## Enter the bootloader in 3 ways:

**Bootmagic reset**: Hold down the key at ESC(0,0) in the matrix (usually the top left key or Escape) and plug in the keyboard
**Physical reset button**: Briefly short the `RESET` and `GND` pads on the SWD header twice, or short the `BOOT` header and plug in keyboard
**Keycode in layout**: Press the key mapped to `QK_BOOT` if it is available