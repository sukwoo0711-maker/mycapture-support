# MyCapture 개인정보처리방침

시행일: 2026-11-08

MyCapture는 화면 캡처, 주석 편집, OCR, 번역, 영역 녹화를 사용자 PC 안에서 처리하는 데스크톱 앱이며 Microsoft Store로 배포합니다.

## 수집하지 않는 정보

MyCapture 개발자는 사용자의 개인정보, 캡처 내용, 사용 기록을 수집하지 않습니다. 앱에는 원격 측정, 분석, 광고 기능이 없고, 오류 정보를 자동으로 보내지 않습니다. 개발자는 사용자가 내용을 확인하고 직접 보낸 문의와 오류 보고만 받습니다.

## PC에 저장되는 정보

다음 정보는 사용자 PC에만 저장되며, 사용자가 아래의 네트워크 기능을 직접 실행하지 않는 한 외부로 보내지 않습니다.

- **캡처 데이터**: 캡처 이미지와 녹화 영상, 썸네일, 주석과 편집 기록, 로컬 OCR로 인식한 텍스트
- **캡처 정보**: 캡처한 창의 제목. 브라우저(Chrome, Edge, Firefox) 화면을 캡처하면 해당 페이지 주소도 함께 저장하며, 이 주소는 PNG 파일의 메타데이터에도 기록될 수 있습니다.
- **핀**: "다음 실행 때 열린 핀 다시 띄우기"가 켜져 있으면(새 설치 기본값) 앱을 끌 때 열려 있던 핀의 이미지와 원문 텍스트(복사한 텍스트·표·코드)를 앱 전용 폴더에 저장하고, 다음 실행 때 다시 띄웁니다. 이 설정을 끄면 저장한 핀을 바로 지웁니다.
- **설정**: 사용자가 입력한 GitHub 토큰을 포함합니다. 토큰은 Windows 데이터 보호 API(DPAPI)로 현재 사용자 계정에 묶어 암호화해 저장합니다. 설정을 내보낼 때는 토큰을 제외합니다.
- **진단 기록**: 문제를 해결하는 데 필요한 값만 담은 로그(모두 합쳐 7MB 이하)와 앱이 예기치 않게 종료된 때의 기록(최대 20개)입니다. 앱과 Windows 버전, 시각, 오류 종류와 오류 코드 같은 값만 기록하며, 캡처 내용, 클립보드, 창 제목, 파일 경로, 입력한 글은 기록하지 않습니다.

## 저장 위치

- 설정, 라이브러리, 진단 로그는 앱 전용 폴더(`%LOCALAPPDATA%\Packages\<패키지 이름>\LocalState`)에 저장합니다. 앱을 제거하면 이 폴더도 함께 삭제됩니다.
- GitHub에서 받은 설치 파일이나 포터블 ZIP으로 설치한 경우에는 `%APPDATA%\MyCapture`에 저장하며, 앱을 제거해도 남습니다.
- 예기치 않은 종료 기록은 `unexpected-exits` 폴더에 저장합니다. 이 폴더는 Microsoft Store 설치본이면 앱 전용 폴더(`%LOCALAPPDATA%\Packages\<패키지 이름>\LocalCache`), GitHub에서 받은 설치 파일이나 포터블 ZIP 설치본이면 `%LOCALAPPDATA%\MyCapture` 안에 있습니다.
- 빠른 저장으로 내보낸 파일은 `사진\Captures` 또는 사용자가 지정한 폴더에 저장되며, 앱을 제거해도 남습니다.

## 네트워크 연결

MyCapture는 다음 경우에만 인터넷에 연결합니다.

1. **OCR 모델 내려받기**
   - 인식 품질이 빠름(기본값)이나 보통이면 Windows에 들어 있는 인식 기능만 쓰므로 아무것도 내려받지 않습니다.
   - 인식 품질이 정확이면 ModelScope(modelscope.cn)에서 공개 PP-OCRv5 모델 파일(약 102MB)을 내려받습니다. 설정에서 정확으로 바꾸면 그때 내려받고, 처음 설치할 때 환영 화면의 "정확한 한국어 글자 인식"을 켜 둔 채 닫으면 첫 실행 뒤 백그라운드에서 내려받습니다. 이 항목은 사양이 충분한 PC(4코어 이상, 메모리 8GB 이상)에서 미리 선택되어 있습니다.
   - 정확으로 둔 동안에는 앱이 시작할 때 빠진 모델 파일이 있는지 확인하고, 없으면 내려받습니다. 데이터 요금제나 로밍 연결, 데이터 한도 초과, 배터리 절약 모드에서는 백그라운드 내려받기를 미룹니다.
   - 4.6.0까지 있던 "가장 정확" 품질은 처음 사용할 때 이미지 확대 모델을 Amazon S3(qaihub-public-assets)에서 내려받습니다. 이후 버전에는 이 품질이 없고, 저장된 "가장 정확" 설정은 정확으로 바뀝니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다.
2. **번역 모델 내려받기**
   - 번역은 기본으로 꺼져 있습니다. 사용자가 OCR 결과 창의 번역 탭에서 "번역 켜기"를 누르거나, 핀의 "번역"을 누르고 설치에 동의할 때만 GitHub(`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`)에서 공개 OPUS-MT 번역 모델 파일을 내려받습니다. 영어→한국어 모델과 한국어→영어 모델이 각각 약 247MB이며, 필요한 방향의 모델만 내려받습니다. 앱이 시작할 때나 백그라운드에서는 내려받지 않습니다.
   - 번역은 사용자 PC 안에서 실행합니다. 번역할 글자와 캡처 이미지는 외부로 보내지 않습니다. 그림 핀은 이 PC의 문자 인식으로 글자를 읽은 뒤 번역합니다.
   - 핀의 번역문은 화면에만 표시하고 저장하지 않습니다. 저장해 둔 핀을 다시 열면 원문으로 엽니다.
   - 내려받은 모델 파일은 크기와 SHA-256으로 확인한 뒤 사용합니다.
   - 내려받은 모델은 Microsoft Store 설치본이면 앱 전용 폴더(`%LOCALAPPDATA%\Packages\<패키지 이름>\LocalCache`), GitHub에서 받은 설치 파일이나 포터블 ZIP 설치본이면 `%LOCALAPPDATA%\MyCapture\translation-models`에 저장합니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다. GitHub로 전달된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
3. **Mermaid 그림 표시**: 핀에 담긴 Markdown의 Mermaid 그림은 Windows의 Microsoft Edge WebView2로 이 PC 안에서 그립니다. MyCapture에 포함된 스크립트만 불러오며, 이 브라우저는 외부 주소에 연결하지 않도록 설정합니다. 그리는 동안 쓰는 브라우저 데이터는 MyCapture 데이터 폴더(GitHub 설치본은 `%APPDATA%\MyCapture\mermaid-browser`)에 둡니다. WebView2 런타임 자체의 업데이트는 Windows와 Microsoft Edge의 정책을 따릅니다.
4. **GitHub 이미지 첨부**: 사용자가 이 기능의 단축키를 눌렀을 때만 동작합니다. 새로 설치하면 단축키가 지정되어 있지 않고, 이전 버전에서 업데이트한 설치는 쓰던 키(이전 기본값 `F9`)를 그대로 씁니다.
   - 토큰을 설정했으면 GitHub API를 통해 이미지를 GitHub에 올립니다. 브라우저 화면을 캡처한 이미지라면 페이지 주소 메타데이터가 함께 전송될 수 있습니다.
   - 토큰이 없으면 설정한 이슈 페이지(기본값은 이 지원 저장소의 새 이슈 페이지)를 기본 브라우저로 열고 이미지를 붙여 넣기만 합니다. 게시 버튼은 누르지 않습니다.
   - GitHub로 전송된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
5. **원본 페이지 열기**: 사용자가 라이브러리에서 저장된 페이지 주소를 열면 기본 브라우저가 그 주소에 연결합니다.
6. **새 버전 확인**: 설정 > 정보의 "새 버전 자동 확인"이 켜져 있으면(기본값) 하루에 한 번 새 버전이 있는지 확인합니다. 이 설정을 끄면 "업데이트 확인"을 누를 때만 확인합니다.
   - Microsoft Store에서 설치한 경우 Microsoft Store를 통해 확인하고 설치합니다.
   - GitHub에서 받은 설치 파일이나 포터블 ZIP으로 설치한 경우 GitHub API(`api.github.com`)에서 최신 릴리스 정보를 확인합니다. 업데이트를 누르면 GitHub(`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`)에서 설치 파일과 해시 목록을 내려받습니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름과 버전이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다. GitHub로 전달된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
7. **문의와 오류 보고**: 사용자가 설정 > 정보의 "문의하기"나 오류 알림의 "오류 보고"를 연 뒤 "GitHub 이슈로 보내기"를 누를 때만 동작합니다.
   - 보낼 내용을 창에서 먼저 보여 줍니다. 환경 정보(앱과 Windows 버전, 화면 배율, 언어, 테마)는 그대로 보내고, 오류 요약과 사용자가 쓴 글은 보내기 전에 고칠 수 있습니다.
   - 확인한 내용을 주소에 담아 이 지원 저장소의 새 이슈 페이지를 기본 브라우저로 엽니다. 이 주소는 페이지가 열릴 때 GitHub로 전달됩니다. 게시 버튼은 누르지 않으며, 이슈는 사용자가 GitHub에서 게시할 때만 공개됩니다.
   - "진단 묶음 저장"은 이 내용과 진단 기록을 사용자가 고른 위치에 ZIP 파일로 저장할 뿐이며 아무것도 보내지 않습니다.
   - GitHub로 전달된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.

Microsoft Store 설치본의 설치와 업데이트는 Microsoft Store가 제공합니다. 이 과정의 정보 처리에는 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/privacystatement)이 적용됩니다.

## 데이터 삭제

- 라이브러리의 항목은 앱 안에서 삭제할 수 있습니다. 새로 설치하면 보관 기간 제한이 없고, 폴더 밖 항목이 1,000개나 5GB를 넘을 때만 오래된 항목부터 자동으로 정리합니다. 보관으로 표시한 항목과 폴더에 넣은 항목은 자동 정리에서 제외합니다.
- 이전 버전에서 업데이트한 설치는 쓰던 설정을 그대로 씁니다. 이전 기본값은 7일이 지난 이미지 정리, 300개, 2GB입니다. 보관 기간과 한도는 설정 > 저장 공간에서 바꿀 수 있습니다.
- GitHub 토큰은 설정에서 지울 수 있습니다.
- 내려받은 번역 모델은 설정에서 삭제할 수 있습니다.
- 진단 로그는 정해진 크기를 넘으면 오래된 파일부터, 예기치 않은 종료 기록은 10개나 64KB를 넘으면 오래된 기록부터 휴지통으로 옮깁니다. `logs`와 `unexpected-exits` 폴더를 지워 직접 삭제할 수도 있습니다.
- 앱을 제거하면 앱 전용 폴더의 설정, 라이브러리, 진단 기록이 삭제됩니다.

## 문의

개인정보 관련 문의는 [support@mimiloaf.com](mailto:support@mimiloaf.com)이나 [이슈](https://github.com/sukwoo0711-maker/mycapture-support/issues)로 보내 주십시오. 보안 문제는 공개 이슈 대신 [비공개 보안 신고](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new)를 이용하십시오.

---

# MyCapture Privacy Policy

Effective date: 2026-11-08

MyCapture is a desktop app, distributed through the Microsoft Store, that captures, annotates, recognizes text in (OCR), translates and records the screen on your PC.

## Information we do not collect

The MyCapture developer does not collect your personal information, capture content or usage history. The app has no telemetry, analytics or advertising and never sends error information automatically. The developer receives only the questions and error reports that you review and send yourself.

## Information stored on your PC

The following stays on your PC and is not sent anywhere unless you use one of the network features below.

- **Capture data**: captured images and recordings, thumbnails, annotations and edits, and text recognized by local OCR.
- **Capture details**: the title of the captured window. When you capture a browser page (Chrome, Edge, Firefox), its address is stored with the capture and may be written into the PNG metadata.
- **Pins**: when "Reopen open pins at the next launch" is on (the default for new installations), the image and original text (copied text, tables or code) of each pin open at exit are saved in the app's package folder and reopened at the next launch. Turning the setting off deletes the saved pins right away.
- **Settings**: including a GitHub token if you enter one. The token is encrypted with the Windows Data Protection API (DPAPI) for your user account and is left out when you export settings.
- **Diagnostic records**: a log that holds only the values needed to solve problems (7 MB in total at most) and a record of each time the app closed unexpectedly (up to 20). They hold values such as the app and Windows versions, times, and error types and codes, and never record capture content, clipboard contents, window titles, file paths or text you type.

## Where data is stored

- Settings, the library and the diagnostic log are kept in the app's package folder (`%LOCALAPPDATA%\Packages\<package name>\LocalState`), which Windows deletes when you uninstall the app.
- Installations from the GitHub setup file or portable ZIP keep them in `%APPDATA%\MyCapture`, which remains after uninstalling.
- Records of unexpected exits are kept in an `unexpected-exits` folder inside the app's package folder (`%LOCALAPPDATA%\Packages\<package name>\LocalCache`) for Microsoft Store installations, or inside `%LOCALAPPDATA%\MyCapture` for installations from the GitHub setup file or portable ZIP.
- Quick-save exports go to `Pictures\Captures` or a folder you choose, and remain after uninstalling.

## Network connections

MyCapture connects to the internet only in these cases:

1. **OCR model download**
   - With recognition quality set to Fast (the default) or Normal, the app uses the recognition built into Windows and downloads nothing.
   - With Accurate, the app downloads the public PP-OCRv5 model files (about 102 MB) from ModelScope (modelscope.cn): when you choose Accurate in Settings, or in the background after the first start if you leave "Accurate Korean text recognition" on in the welcome screen of a new installation. That option is preselected on capable PCs (4 or more cores, 8 GB or more memory).
   - While Accurate stays selected, the app checks for missing model files at startup and downloads any that are missing. Background downloads wait while the connection is metered, roaming or over its data limit, or while battery saver is on.
   - The "Most accurate" quality, available up to version 4.6.0, downloads an image upscaling model from Amazon S3 (qaihub-public-assets) the first time you use it. Later versions no longer offer it and change a saved "Most accurate" setting to Accurate.
   - These requests carry only ordinary HTTP connection data (IP address, a User-Agent with the app name). They never include capture content or personal information.
2. **Translation model download**
   - Translation is off by default. Only when you press **Turn on translation** in the Translate tab of the OCR result window, or press **Translate** on a pin and agree to the install, does MyCapture download the public OPUS-MT translation model files from GitHub (`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`). The English-to-Korean and Korean-to-English models are about 247 MB each, and only the direction you need is downloaded. Nothing is downloaded at startup or in the background.
   - Translation runs on your PC. The text to translate and your captured images are never sent anywhere. For an image pin, MyCapture first reads the text with text recognition on your PC.
   - A pin's translation is only shown on screen and is not saved. A saved pin reopens with its original text.
   - Downloaded model files are checked by size and SHA-256 before use.
   - The model is stored in the app's package folder (`%LOCALAPPDATA%\Packages\<package name>\LocalCache`) for Microsoft Store installations, or in `%LOCALAPPDATA%\MyCapture\translation-models` for installations from the GitHub setup file or portable ZIP.
   - These requests carry only ordinary HTTP connection data (IP address, a User-Agent with the app name). They never include capture content or personal information. [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data that reaches GitHub.
3. **Mermaid diagrams**: Mermaid diagrams in a pin's Markdown are drawn on your PC with Microsoft Edge WebView2 in Windows. Only the script bundled with MyCapture is loaded, and this browser is set not to connect to any outside address. Browser data used while drawing is kept in the MyCapture data folder (`%APPDATA%\MyCapture\mermaid-browser` for GitHub installations). Updates of the WebView2 runtime itself follow Windows and Microsoft Edge policies.
4. **GitHub image attachment**: runs only when you press its shortcut. New installations have no shortcut assigned; installations updated from an earlier version keep their key (the earlier default was `F9`).
   - With a token configured, the image is uploaded to GitHub through its API. For a browser capture, the page address metadata may be included.
   - Without a token, the app opens your configured issue page (by default, a new issue in this support repository) in your default browser and pastes the image without posting it.
   - [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data sent to GitHub.
5. **Opening a source page**: when you open a saved page address from the library, your default browser connects to it.
6. **Checking for new versions**: with "Check for new versions automatically" on in Settings > About (the default), MyCapture checks once a day whether a new version exists. With it off, it checks only when you press **Check for updates**.
   - Microsoft Store installations check and install through the Microsoft Store.
   - Installations from the GitHub setup file or portable ZIP read the latest release information from the GitHub API (`api.github.com`). Pressing **Update** downloads the installer and its hash list from GitHub (`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`).
   - These requests carry only ordinary HTTP connection information (IP address and a User-Agent with the app name and version), never capture content or personal data. [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to what reaches GitHub.
7. **Contact support and error reports**: runs only when you press **Send to GitHub issue** after opening **Contact support** in Settings > About or **Report error** in an error notice.
   - The window shows what will be sent first. Environment details (the app and Windows versions, display scale, language and theme) are sent as shown, and you can edit the error summary and your message before sending.
   - Your default browser then opens a new issue page in this support repository with the text you reviewed in its address. GitHub receives that address when the page opens. The app never presses the post button, and the issue becomes public only when you post it on GitHub.
   - **Save diagnostics bundle** only saves this text and the diagnostic records as a ZIP file where you choose, and sends nothing.
   - [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data that reaches GitHub.

For Microsoft Store installations, installation and updates are provided by the Microsoft Store under the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## Deleting data

- You can delete library items in the app. New installations keep items with no time limit and clean up the oldest items outside folders only after they pass 1,000 items or 5 GB. Items marked Keep and items in folders are never cleaned up automatically.
- Installations updated from an earlier version keep their settings. The earlier defaults were cleanup of images older than 7 days, 300 items and 2 GB. Change the retention period and limits in Settings > Storage.
- You can clear the GitHub token in Settings.
- You can delete the downloaded translation model in Settings.
- The oldest log files move to the Recycle Bin once the log reaches its size limit, and the oldest records of unexpected exits move there once they pass 10 records or 64 KB. You can also delete the `logs` and `unexpected-exits` folders yourself.
- Uninstalling the app deletes the settings, library and diagnostic records in its package folder.

## Contact

Send privacy questions to [support@mimiloaf.com](mailto:support@mimiloaf.com) or through [issues](https://github.com/sukwoo0711-maker/mycapture-support/issues). Report security issues privately through [a security advisory](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new) instead of a public issue.
