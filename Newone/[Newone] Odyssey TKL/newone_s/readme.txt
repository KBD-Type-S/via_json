----------------------------------------------------------------------
 펌웨어 업데이트 방법
----------------------------------------------------------------------

■ 펌웨어 업데이트 절차
1. 아래 3가지 방법 중 하나를 선택하여 키보드를 '부트로더(Bootloader)' 모드로
   진입시킵니다.

2. 정상적으로 진입하면, 컴퓨터의 파일 탐색기에 'RPI-RP2' 라는 이름의
   새로운 드라이브가 나타납니다.

3. 이 드라이브에 준비된 펌웨어 파일(.uf2)을 드래그 앤 드롭 또는
   복사-붙여넣기 합니다. 잠시 후 드라이브가 사라지며 업데이트가
   자동으로 완료됩니다.


■ 부트로더 모드 진입 방법 (3가지)
1. Bootmagic 사용:
   키보드의 가장 왼쪽 위 키(기본 배열에서는 Esc)를 누른 상태로
   PC에 USB 케이블을 연결합니다.

2. 물리적 리셋 사용:
   - 기판(PCB)에 리셋 버튼이 있다면, 해당 버튼을 빠르게 두 번 누릅니다.
   - 또는, 기판의 'RST' 핀과 'GND' 핀을 핀셋 등으로 짧게 두 번 접촉(쇼트)시킵니다.
   - 또는, 'BOOT' 라고 표시된 두 개의 헤더 핀을 쇼트시킨 상태로
     USB 케이블을 연결합니다.

3. 리셋 키코드 사용:
   VIA/VIAL 또는 키맵 코드에서 'QK_BOOT' 또는 'RESET' 키코드로 미리
   설정해 둔 키를 누릅니다.
   (키맵에 해당 기능 키를 미리 할당한 경우에만 사용 가능)



----------------------------------------------------------------------
 Firmware Update Guide
----------------------------------------------------------------------

■ How to Flash Firmware
1. Enter the keyboard's "Bootloader" mode using one of the three methods
   described below.

2. Once in bootloader mode, a new removable drive named "RPI-RP2" will
   appear in your file explorer.

3. Drag and drop (or copy-paste) your firmware file (.uf2) onto this
   drive. The drive will automatically disappear after a moment, and
   the update will be complete.


■ Three Ways to Enter Bootloader Mode
1. Using Bootmagic:
   Hold down the top-left key (usually Esc on the default layout) while
   plugging in the USB cable to your PC.

2. Using Physical Reset:
   - Quickly double-press the physical reset button on the PCB, if one exists.
   - Alternatively, use tweezers to briefly short the 'RST' and 'GND'
     pins on the PCB twice in quick succession.
   - Alternatively, short the two 'BOOT' header pins while plugging in
     the USB cable.

3. Using a Reset Keycode:
   Press the key that you have assigned to 'QK_BOOT' or 'RESET' in your
   keymap (via VIA/VIAL or custom code).
   (This method only works if you have already configured such a key.)