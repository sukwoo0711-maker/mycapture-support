# MyCapture 지원

MyCapture는 개발자를 위한 무료 Windows 캡처·핀 도구입니다. 이 저장소는 사용자 지원과 공개 문서를 위한 곳이며, 앱의 소스 코드는 [my-capture 저장소](https://github.com/sukwoo0711-maker/my-capture)에 있습니다. 기능 소개와 화면은 [MyCapture 웹 페이지](https://mycapture.mimiloaf.com/)에서 볼 수 있습니다.

## 설치

MyCapture는 [Microsoft Store](https://apps.microsoft.com/detail/9PB33MC095VR?cid=support)에서 설치합니다. Store 설치본은 Microsoft가 서명하며, 업데이트도 Microsoft Store가 제공합니다.

- 지원 환경: Windows 11, 또는 Windows 10 버전 22H2(빌드 19045). x64 PC 기준이며, ARM64 PC에서는 Windows 11이 필요합니다.
- 로그인 시 자동 시작은 처음에 꺼져 있으며 설정 > 일반에서 켤 수 있습니다.
- 설정과 라이브러리는 앱 전용 폴더에 저장되며 앱을 제거하면 함께 삭제됩니다. 라이브러리를 유지하려면 설정에서 캡처 폴더를 다른 위치로 지정하십시오.

## Windows 10에서 사용하기

4.3.0부터 Windows 10 버전 22H2(x64)에서 사용할 수 있습니다. 21H2 이하 버전과 ARM64의 Windows 10은 지원하지 않습니다. Windows 10은 2025-10-14에 Microsoft의 일반 지원이 끝났으므로 가능하면 Windows 11을 사용하십시오.

Windows 10에서는 녹화하는 동안 화면 가장자리에 노란 테두리가 보일 수 있습니다. 이 테두리는 녹화 결과에 포함되지 않습니다. 그 밖의 차이는 다음과 같습니다.

| 항목 | Windows 11 | Windows 10 22H2 |
|---|---|---|
| 캡처, 주석, 핀, OCR, 라이브러리, 녹화, GIF 내보내기 | 모두 사용 가능 | 모두 사용 가능 |
| 녹화 중 화면 표시 | 테두리 없음 | 화면 가장자리에 노란 테두리가 보일 수 있음. 녹화 결과에는 포함되지 않음 |
| 녹화 컨트롤, 카운트다운, 알림, 핀 도구 막대 | 반투명 표시 | 불투명 표시. 녹화 결과에서 빠지는 것은 같음 |
| 창 모양 | 둥근 모서리와 창 배경 효과 | 사각 모서리 |
| Print Screen 키 안내 | Windows 11 설정 경로 | Windows 10 설정 경로 |
| ARM64 PC | x64 에뮬레이션으로 실행 | 실행할 수 없음 |

## 문의

문의하는 방법은 네 가지입니다. 편한 쪽을 쓰십시오.

- **메일**: [support@mimiloaf.com](mailto:support@mimiloaf.com)으로 보내 주십시오. GitHub 계정이 없어도 됩니다.
- **GitHub 이슈**: 문제 신고와 기능 제안은 [새 이슈](https://github.com/sukwoo0711-maker/mycapture-support/issues/new)로 남겨 주십시오. Windows 버전, MyCapture 버전, 재현 단계를 함께 적어 주시면 확인이 빠릅니다. Windows 버전은 `Win+R`에서 `winver`를 실행하면 확인할 수 있습니다.
- **Microsoft Store 리뷰**: GitHub 계정이 없으면 [Store의 MyCapture 페이지](https://apps.microsoft.com/detail/9PB33MC095VR?cid=support)에 리뷰를 남겨 주십시오. Microsoft 계정으로 쓸 수 있습니다.
- **앱의 '문의하기' 창**: 4.4.0부터 앱 안의 '문의하기' 창이 앱 버전과 Windows 버전 같은 진단 정보를 채워 줍니다. 내용을 적은 뒤 GitHub 이슈나 Store 리뷰로 보낼 수 있고, 진단 정보만 복사할 수도 있습니다.

캡처 이미지에 개인정보가 보이면 가린 뒤 첨부하십시오. MyCapture의 빠른 가리기(`Ctrl+Shift+R`)를 쓸 수 있습니다. 보안 문제는 공개 이슈에 올리지 말고 [비공개 보안 신고](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new)를 이용하십시오.

## 문서

- [MyCapture 웹 페이지](https://mycapture.mimiloaf.com/)
- 게시자: [Mimiloaf](https://mimiloaf.com/)
- [개인정보처리방침](PRIVACY.md)

---

# MyCapture support

MyCapture is a free Windows screenshot and pinning tool for developers. This repository hosts user support and public documents; the app's source code is in the [my-capture repository](https://github.com/sukwoo0711-maker/my-capture). See features and screenshots on the [MyCapture website](https://mycapture.mimiloaf.com/en/).

It runs on Windows 11 and on Windows 10 version 22H2 (build 19045) x64 PCs. ARM64 PCs need Windows 11. On Windows 10, a yellow border may appear around the screen while recording; it is not included in the recording.

- Install MyCapture from the [Microsoft Store](https://apps.microsoft.com/detail/9PB33MC095VR?cid=support). Updates are delivered by the Store.
- There are four ways to get help:
  - Email [support@mimiloaf.com](mailto:support@mimiloaf.com). No GitHub account is needed.
  - Report problems or suggest features in a [new issue](https://github.com/sukwoo0711-maker/mycapture-support/issues/new), including your Windows version (run `winver`) and MyCapture version.
  - Without a GitHub account, leave a review on the [MyCapture Store page](https://apps.microsoft.com/detail/9PB33MC095VR?cid=support) with your Microsoft account.
  - From 4.4.0, the app's Contact support window fills in diagnostic details such as the app and Windows versions. Write your message, then send it as a GitHub issue or a Store review, or copy the details.
- Report security issues privately through [a security advisory](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new).
- [Privacy policy](PRIVACY.md)
- Publisher: [Mimiloaf](https://mimiloaf.com/en/)
