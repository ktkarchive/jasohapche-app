<div align="center">

# 자소합체 (JasoHapChe)

**macOS 메뉴바에서 한글 파일명을 자동으로 고쳐주는 도구**

[![GitHub Release](https://img.shields.io/github/v/release/ktkarchive/jasohapche-app?style=flat-square)](https://github.com/ktkarchive/jasohapche-app/releases/latest)
[![macOS](https://img.shields.io/badge/macOS-14.0+-blue?style=flat-square&logo=apple)](https://github.com/ktkarchive/jasohapche-app/releases/latest)
[![Universal Binary](https://img.shields.io/badge/Apple%20Silicon%20%2B%20Intel-Universal-orange?style=flat-square)](https://github.com/ktkarchive/jasohapche-app/releases/latest)

[한국어](#한국어) | [English](#english)

</div>

---

## 한국어

### 이게 뭔가요?

Mac에서 만든 한글 파일을 Windows나 Linux로 보내면 이런 일이 생깁니다:

| Mac에서 보이는 이름 | Windows에서 보이는 이름 |
|---|---|
| `한글파일.txt` | `ㅎㅏㄴㄱㅡㄹㅍㅏㅇㅣㄹ.txt` |
| `보고서_최종.pdf` | `ㅂㅗㄱㅗㅅㅓ_ㅊㅗㅇㅇㅈㅗㅇ.pdf` |

이건 macOS가 한글을 **자소 분리(NFD)** 방식으로 저장하기 때문입니다. "한"을 `ㅎ + ㅏ + ㄴ`으로 쪼개서 저장하는 거죠.

**자소합체**는 이 쪼개진 글자들을 다시 합쳐줍니다. 자동으로, 실시간으로.

### 어떻게 동작하나요?

1. 메뉴바에 조용히 상주합니다 (Dock에 안 나타남)
2. 지정한 폴더를 실시간 감시합니다
3. 새 파일이 생기면 한글 이름을 자동으로 NFC(합체)로 변환합니다
4. 끝. 신경 쓸 게 없습니다.

### 메뉴바 아이콘

| 상태 | 아이콘 | 의미 |
|---|---|---|
| 정지 | **분리** | 감시 꺼짐 — 자소가 분리된 상태 |
| 감시 중 | **합체** | 감시 켜짐 — 자소를 합체하는 중 |

### 주요 기능

- **복수 폴더 감시** — 여러 폴더를 등록하고 개별 on/off
- **재귀 감시** — 하위 폴더까지 자동 포함
- **안전한 처리** — 파일 복사 중에는 건드리지 않음 (안정화 지연)
- **충돌 방지** — 같은 이름이 이미 있으면 `파일 (1).txt` 형태로 자동 저장
- **동기화 폴더 보호** — Dropbox, iCloud, OneDrive 등은 기본 제외 (충돌 방지)
- **3가지 디자인** — 간결한 메뉴 / 상태 패널 / 토글 그리드 중 선택
- **처리 로그** — 무엇이 변환되었는지 확인 가능

### 설치

1. [Releases](https://github.com/ktkarchive/jasohapche-app/releases/latest) 에서 `JasoHapChe-x.x.x.zip` 다운로드
2. 압축 해제
3. `자소합체.app`을 `/Applications` 폴더로 이동
4. **처음 실행 전** 터미널에서 격리 속성 제거:
   ```bash
   xattr -cr /Applications/자소합체.app
   ```
5. 실행

### 시스템 요구사항

- macOS 14 (Sonoma) 이상
- Apple Silicon (M1/M2/M3/M4) 및 Intel Mac 모두 지원

### 제외 규칙 (기본)

자동으로 무시하는 항목:
- 숨김 파일/폴더 (`.`으로 시작)
- 임시 파일 (`.tmp`, `.part`, `.crdownload`)
- 시스템 폴더 (`.git`, `.svn`, `.hg`)
- 심볼릭 링크

설정에서 확장자/폴더를 추가로 제외할 수 있습니다.

---

## English

### What is this?

When you create files with Korean names on macOS and transfer them to Windows or Linux, the filenames can appear broken:

| Name on Mac | Name on Windows |
|---|---|
| `한글파일.txt` | `ㅎㅏㄴㄱㅡㄹㅍㅏㅇㅣㄹ.txt` |
| `보고서_최종.pdf` | `ㅂㅗㄱㅗㅅㅓ_ㅊㅗㅇㅇㅈㅗㅇ.pdf` |

This happens because macOS stores Korean characters in **NFD (decomposed)** form — splitting "한" into `ㅎ + ㅏ + ㄴ` as separate Unicode code points.

**JasoHapChe** automatically recomposes these decomposed characters back into their proper NFC form. In real-time, silently.

### How does it work?

1. Lives quietly in your menu bar (no Dock icon)
2. Watches folders you specify in real-time
3. Automatically converts Korean filenames from NFD to NFC when new files appear
4. That's it. Set it and forget it.

### Menu Bar Icon

| State | Icon | Meaning |
|---|---|---|
| Stopped | **분리** (Decomposed) | Watching is off |
| Watching | **합체** (Composed) | Actively fixing filenames |

### Key Features

- **Multiple folder watch** — Register multiple folders, toggle each on/off
- **Recursive watch** — Automatically includes subfolders
- **Safe processing** — Waits for file copy to complete before renaming (stabilization delay)
- **Conflict resolution** — If a file with the same name exists, auto-appends `(1)`, `(2)`, etc.
- **Sync folder protection** — Dropbox, iCloud, OneDrive folders are excluded by default
- **3 UI designs** — Simple menu / Status panel / Toggle grid
- **Processing log** — See what was converted and when

### Installation

1. Download `JasoHapChe-x.x.x.zip` from [Releases](https://github.com/ktkarchive/jasohapche-app/releases/latest)
2. Unzip
3. Move `자소합체.app` to `/Applications`
4. **Before first launch**, remove quarantine attribute in Terminal:
   ```bash
   xattr -cr /Applications/자소합체.app
   ```
5. Run

### System Requirements

- macOS 14 (Sonoma) or later
- Supports both Apple Silicon (M1/M2/M3/M4) and Intel Macs (Universal Binary)

### Default Exclusions

Automatically ignored:
- Hidden files/folders (starting with `.`)
- Temporary files (`.tmp`, `.part`, `.crdownload`)
- System folders (`.git`, `.svn`, `.hg`)
- Symbolic links

You can add custom extensions/folders to exclude in Settings.

---

## License

MIT License
