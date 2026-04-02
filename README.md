# 자소합체 (JasoHapChe)

macOS 메뉴바에서 파일/폴더 이름의 한글 유니코드를 자동으로 정규화(NFC)하는 도구입니다.

## 문제

macOS에서 생성된 일부 한글 파일명이 NFD(자소 분리) 형태가 되어, Windows/Linux에서 검색이 안 되거나 깨져 보이는 문제가 있습니다.

## 해결

자소합체는 지정 폴더를 실시간 감시하여 NFD 한글 파일명을 자동으로 NFC로 변환합니다.

## 기능

- 메뉴바 상주 (Dock 아이콘 없음)
- 복수 폴더 감시 (on/off, 재귀 감시)
- 한글 포함 파일명만 정규화 (옵션: 전체 유니코드)
- 충돌 시 자동 suffix 부여
- 안정화 지연 (복사 중 파일 보호)
- 동기화 폴더 기본 제외 + 경고
- 3가지 메뉴바 디자인 선택 가능
- 처리 로그 확인

## 설치

[Releases](https://github.com/ktkarchive/jasohapche-app/releases) 페이지에서 최신 버전을 다운로드하세요.

1. `JasoHapChe.app.zip` 다운로드
2. 압축 해제
3. `JasoHapChe.app`을 `/Applications`로 이동
4. 실행

## 시스템 요구사항

- macOS 14 (Sonoma) 이상

## 라이선스

MIT License
