# MyCapture 개인정보처리방침

시행일: 2026-10-21

MyCapture는 화면 캡처, 주석 편집, OCR, 영역 녹화를 사용자 PC 안에서 처리하는 데스크톱 앱이며 Microsoft Store로 배포합니다.

## 수집하지 않는 정보

MyCapture 개발자는 사용자의 개인정보, 캡처 내용, 사용 기록을 수집하거나 전송받지 않습니다. 앱에는 원격 측정, 분석, 광고, 충돌 보고 기능이 없습니다.

## PC에 저장되는 정보

다음 정보는 사용자 PC에만 저장되며, 사용자가 아래의 네트워크 기능을 직접 실행하지 않는 한 외부로 보내지 않습니다.

- **캡처 데이터**: 캡처 이미지와 녹화 영상, 썸네일, 주석과 편집 기록, 로컬 OCR로 인식한 텍스트
- **캡처 정보**: 캡처한 창의 제목. 브라우저(Chrome, Edge, Firefox) 화면을 캡처하면 해당 페이지 주소도 함께 저장하며, 이 주소는 PNG 파일의 메타데이터에도 기록될 수 있습니다.
- **핀**: "다음 실행 때 열린 핀 다시 띄우기"가 켜져 있으면(새 설치 기본값) 앱을 끌 때 열려 있던 핀의 이미지와 원문 텍스트(복사한 텍스트·표·코드)를 앱 전용 폴더에 저장하고, 다음 실행 때 다시 띄웁니다. 이 설정을 끄면 저장한 핀을 바로 지웁니다.
- **설정**: 사용자가 입력한 GitHub 토큰을 포함합니다. 토큰은 Windows 데이터 보호 API(DPAPI)로 현재 사용자 계정에 묶어 암호화해 저장합니다. 설정을 내보낼 때는 토큰을 제외합니다.

## 저장 위치

- 설정과 라이브러리는 앱 전용 폴더(`%LOCALAPPDATA%\Packages\<패키지 이름>\LocalState`)에 저장합니다. 앱을 제거하면 이 폴더도 함께 삭제됩니다.
- 빠른 저장으로 내보낸 파일은 `사진\Captures` 또는 사용자가 지정한 폴더에 저장되며, 앱을 제거해도 남습니다.

## 네트워크 연결

MyCapture는 다음 경우에만 인터넷에 연결합니다.

1. **OCR 모델 내려받기**
   - 인식 품질이 빠름(기본값)이나 보통이면 Windows에 들어 있는 인식 기능만 쓰므로 아무것도 내려받지 않습니다.
   - 설정에서 인식 품질을 정확이나 가장 정확으로 바꾸면, 그 품질로 처음 인식할 때 ModelScope(modelscope.cn)에서 공개 모델 파일을 내려받습니다. 그 품질로 둔 동안에는 앱이 시작할 때 빠진 모델 파일이 있는지 확인하고, 없으면 내려받습니다.
   - 가장 정확에서 쓰는 이미지 확대 모델은 처음 사용할 때 Amazon S3(qaihub-public-assets)에서 내려받습니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다.
2. **GitHub 이미지 첨부**: 사용자가 이 기능의 단축키를 눌렀을 때만 동작합니다. 새로 설치하면 단축키가 지정되어 있지 않고, 이전 버전에서 업데이트한 설치는 쓰던 키(이전 기본값 `F9`)를 그대로 씁니다.
   - 토큰을 설정했으면 GitHub API를 통해 이미지를 GitHub에 올립니다. 브라우저 화면을 캡처한 이미지라면 페이지 주소 메타데이터가 함께 전송될 수 있습니다.
   - 토큰이 없으면 설정한 이슈 페이지(기본값은 이 지원 저장소의 새 이슈 페이지)를 기본 브라우저로 열고 이미지를 붙여 넣기만 합니다. 게시 버튼은 누르지 않습니다.
   - GitHub로 전송된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
3. **원본 페이지 열기**: 사용자가 라이브러리에서 저장된 페이지 주소를 열면 기본 브라우저가 그 주소에 연결합니다.

설치와 업데이트는 Microsoft Store가 제공합니다. 이 과정의 정보 처리에는 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/privacystatement)이 적용됩니다.

## 데이터 삭제

- 라이브러리의 항목은 앱 안에서 삭제할 수 있습니다. 새로 설치하면 보관 기간 제한이 없고, 폴더 밖 항목이 1,000개나 5GB를 넘을 때만 오래된 항목부터 자동으로 정리합니다. 보관으로 표시한 항목과 폴더에 넣은 항목은 자동 정리에서 제외합니다.
- 이전 버전에서 업데이트한 설치는 쓰던 설정을 그대로 씁니다. 이전 기본값은 7일이 지난 이미지 정리, 300개, 2GB입니다. 보관 기간과 한도는 설정 > 저장 공간에서 바꿀 수 있습니다.
- GitHub 토큰은 설정에서 지울 수 있습니다.
- 앱을 제거하면 앱 전용 폴더의 설정과 라이브러리가 삭제됩니다.

## 문의

개인정보 관련 문의는 [이슈](https://github.com/sukwoo0711-maker/mycapture-support/issues)로 보내 주십시오. 보안 문제는 공개 이슈 대신 [비공개 보안 신고](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new)를 이용하십시오.

---

# MyCapture Privacy Policy

Effective date: 2026-10-21

MyCapture is a desktop app, distributed through the Microsoft Store, that captures, annotates, recognizes text in (OCR) and records the screen on your PC.

## Information we do not collect

The MyCapture developer does not collect or receive your personal information, capture content or usage history. The app has no telemetry, analytics, advertising or crash reporting.

## Information stored on your PC

The following stays on your PC and is not sent anywhere unless you use one of the network features below.

- **Capture data**: captured images and recordings, thumbnails, annotations and edits, and text recognized by local OCR.
- **Capture details**: the title of the captured window. When you capture a browser page (Chrome, Edge, Firefox), its address is stored with the capture and may be written into the PNG metadata.
- **Pins**: when "Reopen open pins at the next launch" is on (the default for new installations), the image and original text (copied text, tables or code) of each pin open at exit are saved in the app's package folder and reopened at the next launch. Turning the setting off deletes the saved pins right away.
- **Settings**: including a GitHub token if you enter one. The token is encrypted with the Windows Data Protection API (DPAPI) for your user account and is left out when you export settings.

## Where data is stored

- Settings and the library are kept in the app's package folder (`%LOCALAPPDATA%\Packages\<package name>\LocalState`), which Windows deletes when you uninstall the app.
- Quick-save exports go to `Pictures\Captures` or a folder you choose, and remain after uninstalling.

## Network connections

MyCapture connects to the internet only in these cases:

1. **OCR model download**
   - With recognition quality set to Fast (the default) or Normal, the app uses the recognition built into Windows and downloads nothing.
   - If you choose Accurate or Most accurate in Settings, the app downloads public model files from ModelScope (modelscope.cn) the first time it recognizes text at that quality. While either quality stays selected, it checks for missing model files at startup and downloads any that are missing.
   - The image upscaling model used by Most accurate is downloaded from Amazon S3 (qaihub-public-assets) the first time you use it.
   - These requests carry only ordinary HTTP connection data (IP address, a User-Agent with the app name). They never include capture content or personal information.
2. **GitHub image attachment**: runs only when you press its shortcut. New installations have no shortcut assigned; installations updated from an earlier version keep their key (the earlier default was `F9`).
   - With a token configured, the image is uploaded to GitHub through its API. For a browser capture, the page address metadata may be included.
   - Without a token, the app opens your configured issue page (by default, a new issue in this support repository) in your default browser and pastes the image without posting it.
   - [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data sent to GitHub.
3. **Opening a source page**: when you open a saved page address from the library, your default browser connects to it.

Installation and updates are provided by the Microsoft Store under the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## Deleting data

- You can delete library items in the app. New installations keep items with no time limit and clean up the oldest items outside folders only after they pass 1,000 items or 5 GB. Items marked Keep and items in folders are never cleaned up automatically.
- Installations updated from an earlier version keep their settings. The earlier defaults were cleanup of images older than 7 days, 300 items and 2 GB. Change the retention period and limits in Settings > Storage.
- You can clear the GitHub token in Settings.
- Uninstalling the app deletes the settings and library in its package folder.

## Contact

Send privacy questions through [issues](https://github.com/sukwoo0711-maker/mycapture-support/issues). Report security issues privately through [a security advisory](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new) instead of a public issue.
