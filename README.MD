# QMK / VIA JSON Archive

**한국어** | [English](README.EN.md)

키보드와 PCB의 QMK·VIA 관련 JSON 파일을 모아 보존하는 커뮤니티 아카이브입니다.

제조사 웹사이트, 판매 페이지, Discord 등에 흩어져 있는 자료를 한곳에서 찾고, 원래 배포 경로가 사라진 뒤에도 키보드를 계속 사용할 수 있도록 하는 것을 목표로 합니다.

## 목적

- **자료의 장기 보존**: 사이트 폐쇄, 도메인 만료, Discord 서버·채널 삭제, 첨부파일 링크 만료로 인한 파일 소실에 대비합니다.
- **접근성 개선**: 제조사마다 다른 다운로드 경로를 찾거나 여러 Discord 서버에 가입해야 하는 불편을 줄입니다.
- **구형 제품의 지속적인 사용**: 단종 제품이나 지원이 종료된 PCB도 필요한 자료를 확보해 설정하고 유지할 수 있도록 돕습니다.
- **버전과 변형 보존**: PCB Revision, 연결 방식, Hot-swap·Solder 등의 차이에 따른 자료를 구분하고, 업데이트 전 파일도 추적할 수 있도록 합니다.
- **출처와 호환 정보 공유**: 파일의 배포처와 적용 대상을 함께 기록해 잘못된 파일을 선택하는 일을 줄입니다.
- **커뮤니티 지식 축적**: 개인이 보관하던 자료와 사용 중 확인한 정보를 공유해 반복적인 파일 요청과 검색을 줄입니다.

이 저장소는 독립적인 아카이브입니다. 파일이 이곳에 있다는 사실이 QMK 또는 VIA의 공식 지원 등록이나 모든 하드웨어에서의 동작 검증을 의미하지는 않습니다.

## 파일 종류와 용어

`.json`은 파일 형식이며, 모든 JSON 파일이 같은 용도로 사용되는 것은 아닙니다. 파일명만으로 판단하지 말고 내용과 원래 배포 안내를 확인하세요.

| 명칭 | 역할 | 사용하는 곳 |
| --- | --- | --- |
| **VIA Keyboard Definition** | 키보드 식별 정보, Matrix, 물리적 Layout과 Layout Options, 지원하는 설정 UI 등을 정의합니다. | VIA의 `Design` 탭에서 불러옵니다. |
| **QMK Keymap JSON** | QMK의 키보드 식별자, Layout Macro, Layer별 Keycode 등 Keymap을 기술합니다. | QMK Configurator 또는 QMK CLI에서 사용합니다. |
| **VIA에서 저장한 Layout JSON** | VIA에서 저장한 키 할당 등 사용자 설정을 담습니다. | VIA의 `Save Current Layout` / `Load Saved Layout` 기능으로 저장·복원합니다. |
| **QMK의 `info.json` / `keyboard.json`** | QMK Firmware의 키보드 하드웨어·Layout 등 Data Driven Configuration에 사용됩니다. | QMK 소스 및 빌드 환경에서 사용하며, VIA Keyboard Definition과 구분해야 합니다. |

위 표는 JSON 종류를 구분하기 위한 안내이며, 모든 종류가 이 저장소의 모든 모델에 제공된다는 뜻은 아닙니다.

> VIA Keyboard Definition은 펌웨어가 아닙니다. JSON 파일을 불러오는 것만으로 키보드에 VIA 지원이 추가되거나 펌웨어가 업데이트되지는 않습니다. 또한 VIA Keyboard Definition의 `layouts.keymap`은 물리적 키 위치와 Matrix 좌표를 나타내며, QMK Keymap JSON의 `layers`에 기록하는 Keycode 할당과는 용도가 다릅니다.

## 폴더 구조

기본적으로 **제조사·브랜드 → 키보드 또는 PCB 모델 → 관련 파일** 순서로 정리합니다. 일부 모델은 버전이나 PCB 종류에 따라 추가 하위 폴더를 가질 수 있습니다.

| 경로 또는 패턴 | 설명 |
| --- | --- |
| `<제조사 또는 브랜드>/` | 제조사·브랜드별 최상위 폴더입니다. 예: `Geonworks/`, `QwertyKeys/`, `TKD/`. |
| `<제조사 또는 브랜드>/[제조사 또는 브랜드] <모델명>/` | 해당 키보드 또는 PCB의 자료를 보관합니다. |
| `ETC/` | 기타 자료를 확인할 수 있는 폴더입니다. |
| `README.MD` | 저장소의 목적, 파일 구분, 사용 방법과 기여 안내입니다. |
| `README.EN.md` | 영문 README입니다. |

현재 저장소에서 확인할 수 있는 경로의 예시는 다음과 같습니다.

| 예시 경로 | 설명 |
| --- | --- |
| `Alexotos/[Alexotos] Manta65/` | Alexotos의 Manta65 자료 |
| `Cidoo/[Cidoo] ABM066/` | Cidoo의 ABM066 자료 |
| `GDK Lab/[GDK Lab] KV1-65/kv1-65_hotswap_wired.json` | KV1-65의 Hot-swap·유선용 VIA Keyboard Definition |
| `TKD/[TKD] Pt.1-75/TKD - Pt.1-75 Solderable.json` | Pt.1-75의 Solder용 VIA Keyboard Definition |

GitHub가 중간 폴더를 하나의 경로처럼 표시하더라도 실제로는 제조사 폴더와 모델 폴더로 나뉩니다. 새 자료는 기존 분류와 파일명을 우선 확인한 뒤 추가해 주세요.

## 사용 전 요구사항

### 공통 확인 사항

- 키보드 모델명뿐 아니라 **실제로 장착된 PCB 모델과 Revision**을 확인합니다. 같은 케이스에 다른 PCB가 장착되어 있을 수 있습니다.
- Hot-swap·Solder, ANSI·ISO, 유선·무선 등 배포처가 구분한 변형에 맞는 파일을 선택합니다.
- 파일의 출처, 대상 펌웨어, 버전 안내가 있다면 함께 확인합니다. 최신 파일이 모든 구형 PCB에 맞는 것은 아닙니다.

### VIA Keyboard Definition 사용 시

- 키보드에 **VIA를 지원하는 펌웨어**가 설치되어 있어야 합니다. QMK Firmware 사용 여부만으로 VIA 지원을 단정할 수 없습니다.
- [VIA 웹 앱](https://usevia.app/)을 사용하려면 WebHID를 지원하는 브라우저와 장치 접근 권한이 필요합니다. 지원 환경에서는 Chrome 또는 Edge 등을 사용할 수 있습니다.
- 펌웨어가 지원하는 연결 방식을 사용해야 합니다. Bluetooth나 2.4 GHz 연결 상태에서도 VIA 설정이 가능한지는 모델별로 다르므로 제조사 안내를 확인하세요.
- Definition의 USB Vendor ID(`vendorId`)·Product ID(`productId`), Matrix 및 Layout이 대상 펌웨어와 일치해야 합니다. VID/PID 일치만으로 전체 호환성이 보장되지는 않습니다.
- V2·V3 Definition은 대상 펌웨어와 배포 안내에 맞춰 선택합니다. Definition 버전과 VIA Firmware Protocol 버전은 구분해야 합니다.

### QMK Keymap JSON 사용 시

- [QMK Configurator](https://config.qmk.fm/) 또는 QMK CLI와 필요한 빌드 환경을 준비합니다.
- JSON이 지정한 `keyboard`, `layout` 및 Keycode를 사용하는 QMK 버전에서 지원해야 합니다.
- QMK Configurator에서 지원하지 않는 제조사 전용 키보드나 Fork는 해당 제조사가 안내하는 소스와 빌드 환경이 필요할 수 있습니다.

단순히 자료를 다운로드하고 보관하는 데에는 QMK 빌드 환경이 필요하지 않습니다.

## 사용 방법

### 1. 파일 찾기와 다운로드

1. 제조사·브랜드 폴더에서 키보드 또는 PCB 모델을 찾습니다. GitHub의 `Go to file`로 검색할 수도 있습니다.
2. PCB 종류, Revision, 연결 방식 및 버전이 맞는 파일을 선택합니다.
3. 파일 페이지의 `Download raw file`로 다운로드합니다. 웹페이지를 HTML로 저장하지 않도록 주의하세요.

전체 자료를 보관하려면 저장소의 `Code` → `Download ZIP`을 사용하거나 Git으로 복제할 수 있습니다.

```sh
git clone https://github.com/KBD-Type-S/via_json.git
```

### 2. VIA Keyboard Definition 불러오기

VIA가 이미 키보드를 정상적으로 인식한다면 별도의 Definition을 수동으로 불러올 필요가 없을 수 있습니다.

1. [VIA](https://usevia.app/)를 열고, 제조사가 안내하는 방식으로 키보드를 연결합니다.
2. `Settings`에서 `Show Design tab`을 활성화합니다.
3. `Design` 탭의 `Load Draft Definition`에 있는 `Load`로 해당 VIA Keyboard Definition을 선택합니다.
4. V2 Definition을 사용하고 현재 앱에 `Use V2 definitions` 옵션이 있다면 배포 안내에 맞게 설정합니다.
5. `Configure` 탭에서 장치를 연결·승인한 뒤, 표시된 Layout과 Layout Options가 실제 키보드와 일치하는지 확인합니다.
6. 기존 설정을 보존하려면 변경 전에 `Save Current Layout`으로 백업합니다.

앱 버전과 표시 언어에 따라 메뉴 이름이나 위치가 달라질 수 있습니다. QMK Keymap JSON이나 VIA에서 저장한 Layout JSON을 `Load Draft Definition`에 넣지 마세요.

### 3. QMK Keymap JSON 사용하기

QMK Configurator의 Keymap JSON 불러오기 기능을 사용하거나, QMK CLI에서 다음과 같이 빌드할 수 있습니다. `path/to/keymap.json`은 실제 파일 경로로 바꿔 사용하세요.

```sh
qmk compile path/to/keymap.json
```

빌드한 펌웨어의 Flashing은 PCB의 MCU와 Bootloader에 맞는 절차를 따라야 합니다. 이 저장소의 파일을 받았다는 이유만으로 Flashing이 필요한 것은 아닙니다.

## 문제 해결

| 증상 | 확인할 사항 |
| --- | --- |
| VIA에서 장치가 보이지 않음 | VIA 지원 펌웨어, 데이터 전송 가능한 케이블, 연결 모드, 브라우저의 WebHID 지원 및 장치 권한을 확인합니다. Linux에서는 장치 접근을 위한 udev 설정이 필요할 수 있습니다. |
| Definition을 불러와도 인식되지 않음 | PCB Revision, VID/PID, V2·V3 Definition과 펌웨어의 대응 여부를 확인합니다. |
| JSON을 불러올 때 오류 발생 | HTML 페이지를 저장하지 않았는지, 올바른 종류의 JSON인지, 해당 앱이 파일 형식을 지원하는지 확인합니다. |
| Layout이 다르거나 키 위치가 맞지 않음 | 다른 PCB용 파일을 선택했는지, Hot-swap·Solder 등의 변형과 Layout Options가 맞는지 확인합니다. |
| RGB Lighting이나 Encoder가 설정대로 작동하지 않음 | Definition이 표시하는 기능을 펌웨어에서도 지원하는지, 해당 펌웨어용 Definition이 맞는지 확인합니다. |

인식되지 않는 장치를 연결하려고 VID/PID나 Matrix 값을 임의로 변경하기보다, 대상 PCB와 펌웨어에 맞는 자료부터 확인하세요.

## 자료 추가와 수정

누락된 파일, 새 버전, 출처 정보, 잘못 분류된 자료 또는 호환성 문제는 [Issue](https://github.com/KBD-Type-S/via_json/issues)나 [Pull Request](https://github.com/KBD-Type-S/via_json/pulls)로 알려 주세요.

### 추가 시 권장 사항

- 기존 제조사·모델 폴더가 있는지 먼저 확인합니다.
- 원본 파일명과 내용을 가능한 한 유지합니다. 구분이 필요하면 PCB 종류·Revision·버전을 파일명이나 하위 폴더로 명확히 표시합니다.
- 새 버전이 나와도 이전 파일을 곧바로 덮어쓰지 말고, 구형 PCB나 펌웨어에서 필요한 버전인지 확인합니다.
- 원본을 수정한 파일은 원본과 구분하고 수정 내용과 이유를 기록합니다.
- JSON 문법 검사와 실물 동작 확인을 구분해 기록합니다. 문법이 올바르다고 하드웨어 호환성이 검증된 것은 아닙니다.
- 재배포 조건을 확인하고, 개인정보나 공개가 제한된 내용을 함께 올리지 않도록 합니다.

아래 정보를 PR 본문이나 모델 폴더의 README에 남기면 이후 사용자가 파일을 선택하는 데 도움이 됩니다. 알 수 없는 정보는 추정하지 말고 `미확인`으로 표시해 주세요.

| 항목 | 기록할 내용 |
| --- | --- |
| 제조사·모델 | 키보드 모델 및 PCB 모델 |
| 하드웨어 구분 | PCB Revision, Hot-swap·Solder, 연결 방식 등 |
| 파일 종류 | VIA Keyboard Definition, QMK Keymap JSON 등 |
| 출처 | 원문 URL, 제조사 다운로드 페이지 또는 Discord 메시지 링크 |
| 보존 시점 | 파일을 확보한 날짜, 배포일 또는 제공된 버전 |
| 호환 정보 | 대상 펌웨어 버전, Definition V2·V3, 필요한 사용 조건 |
| 검증 상태 | 미검증 / JSON 문법 확인 / 특정 PCB·펌웨어에서 동작 확인 |
| 변경 사항 | 원본 여부, 수정 내용, 이전 버전과의 차이 |
| 권리 정보 | 원본 라이선스 또는 재배포 허용 조건 |

## 출처와 권리

각 파일의 제작자·제조사와 원래 배포처를 존중합니다. 아카이빙을 위해 수집된 자료라도 원본의 라이선스와 재배포 조건이 적용되며, 저장소에 올라와 있다는 사실만으로 자유로운 수정·재배포가 허용되는 것은 아닙니다.

출처 표기, 파일 수정 또는 삭제가 필요한 경우 해당 파일 경로와 사유를 Issue로 알려 주세요.

## 공식 문서

- [QMK Firmware 문서](https://docs.qmk.fm/)
- [QMK Configurator: Step by Step](https://docs.qmk.fm/configurator_step_by_step)
- [QMK Keymap JSON 형식](https://docs.qmk.fm/configurator_default_keymaps)
- [QMK CLI Commands](https://docs.qmk.fm/cli_commands)
- [VIA Specification — Keyboard Definition](https://www.caniusevia.com/docs/specification/)
- [VIA — Configuring QMK](https://www.caniusevia.com/docs/configuring_qmk/)
- [VIA 앱 소스](https://github.com/the-via/app)
- [VIA 공식 Keyboard Definitions 저장소](https://github.com/the-via/keyboards)
