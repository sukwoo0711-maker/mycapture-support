# MyCapture 개인정보처리방침

시행일: 2026-10-25

MyCapture는 화면 캡처, 주석 편집, OCR, 번역, 영역 녹화를 사용자 PC 안에서 처리하는 데스크톱 앱이며 Microsoft Store로 배포합니다.

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
- GitHub에서 받은 설치 파일이나 포터블 ZIP으로 설치한 경우에는 `%APPDATA%\MyCapture`에 저장하며, 앱을 제거해도 남습니다.
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
   - 번역은 기본으로 꺼져 있습니다. 사용자가 OCR 결과 창의 번역 탭에서 "번역 켜기"를 누를 때만 GitHub(`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`)에서 공개 OPUS-MT 영어→한국어 번역 모델 파일(약 247MB)을 내려받습니다. 앱이 시작할 때나 백그라운드에서는 내려받지 않습니다.
   - 번역은 사용자 PC 안에서 실행합니다. 번역할 글자와 캡처 이미지는 외부로 보내지 않습니다.
   - 내려받은 모델은 Microsoft Store 설치본이면 앱 전용 폴더(`%LOCALAPPDATA%\Packages\<패키지 이름>\LocalCache`), GitHub에서 받은 설치 파일이나 포터블 ZIP 설치본이면 `%LOCALAPPDATA%\MyCapture\translation-models`에 저장합니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다. GitHub로 전달된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
3. **GitHub 이미지 첨부**: 사용자가 이 기능의 단축키를 눌렀을 때만 동작합니다. 새로 설치하면 단축키가 지정되어 있지 않고, 이전 버전에서 업데이트한 설치는 쓰던 키(이전 기본값 `F9`)를 그대로 씁니다.
   - 토큰을 설정했으면 GitHub API를 통해 이미지를 GitHub에 올립니다. 브라우저 화면을 캡처한 이미지라면 페이지 주소 메타데이터가 함께 전송될 수 있습니다.
   - 토큰이 없으면 설정한 이슈 페이지(기본값은 이 지원 저장소의 새 이슈 페이지)를 기본 브라우저로 열고 이미지를 붙여 넣기만 합니다. 게시 버튼은 누르지 않습니다.
   - GitHub로 전송된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.
4. **원본 페이지 열기**: 사용자가 라이브러리에서 저장된 페이지 주소를 열면 기본 브라우저가 그 주소에 연결합니다.
5. **새 버전 확인**: 설정 > 정보의 "새 버전 자동 확인"이 켜져 있으면(기본값) 하루에 한 번 새 버전이 있는지 확인합니다. 이 설정을 끄면 "업데이트 확인"을 누를 때만 확인합니다.
   - Microsoft Store에서 설치한 경우 Microsoft Store를 통해 확인하고 설치합니다.
   - GitHub에서 받은 설치 파일이나 포터블 ZIP으로 설치한 경우 GitHub API(`api.github.com`)에서 최신 릴리스 정보를 확인합니다. 업데이트를 누르면 GitHub(`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`)에서 설치 파일과 해시 목록을 내려받습니다.
   - 이 요청에는 일반적인 HTTP 연결 정보(IP 주소, 앱 이름과 버전이 담긴 User-Agent)만 전달됩니다. 캡처 내용이나 개인정보는 포함되지 않습니다. GitHub로 전달된 정보에는 [GitHub 개인정보처리방침](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement)이 적용됩니다.

Microsoft Store 설치본의 설치와 업데이트는 Microsoft Store가 제공합니다. 이 과정의 정보 처리에는 [Microsoft 개인정보처리방침](https://privacy.microsoft.com/privacystatement)이 적용됩니다.

## 데이터 삭제

- 라이브러리의 항목은 앱 안에서 삭제할 수 있습니다. 새로 설치하면 보관 기간 제한이 없고, 폴더 밖 항목이 1,000개나 5GB를 넘을 때만 오래된 항목부터 자동으로 정리합니다. 보관으로 표시한 항목과 폴더에 넣은 항목은 자동 정리에서 제외합니다.
- 이전 버전에서 업데이트한 설치는 쓰던 설정을 그대로 씁니다. 이전 기본값은 7일이 지난 이미지 정리, 300개, 2GB입니다. 보관 기간과 한도는 설정 > 저장 공간에서 바꿀 수 있습니다.
- GitHub 토큰은 설정에서 지울 수 있습니다.
- 내려받은 번역 모델은 설정에서 삭제할 수 있습니다.
- 앱을 제거하면 앱 전용 폴더의 설정과 라이브러리가 삭제됩니다.

## 문의

개인정보 관련 문의는 [support@mimiloaf.com](mailto:support@mimiloaf.com)이나 [이슈](https://github.com/sukwoo0711-maker/mycapture-support/issues)로 보내 주십시오. 보안 문제는 공개 이슈 대신 [비공개 보안 신고](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new)를 이용하십시오.

---

# MyCapture Privacy Policy

Effective date: 2026-10-25

MyCapture is a desktop app, distributed through the Microsoft Store, that captures, annotates, recognizes text in (OCR), translates and records the screen on your PC.

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
- Installations from the GitHub setup file or portable ZIP keep them in `%APPDATA%\MyCapture`, which remains after uninstalling.
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
   - Translation is off by default. Only when you press **Turn on translation** in the Translate tab of the OCR result window does MyCapture download the public OPUS-MT English-to-Korean translation model files (about 247 MB) from GitHub (`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`). Nothing is downloaded at startup or in the background.
   - Translation runs on your PC. The text to translate and your captured images are never sent anywhere.
   - The model is stored in the app's package folder (`%LOCALAPPDATA%\Packages\<package name>\LocalCache`) for Microsoft Store installations, or in `%LOCALAPPDATA%\MyCapture\translation-models` for installations from the GitHub setup file or portable ZIP.
   - These requests carry only ordinary HTTP connection data (IP address, a User-Agent with the app name). They never include capture content or personal information. [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data that reaches GitHub.
3. **GitHub image attachment**: runs only when you press its shortcut. New installations have no shortcut assigned; installations updated from an earlier version keep their key (the earlier default was `F9`).
   - With a token configured, the image is uploaded to GitHub through its API. For a browser capture, the page address metadata may be included.
   - Without a token, the app opens your configured issue page (by default, a new issue in this support repository) in your default browser and pastes the image without posting it.
   - [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to data sent to GitHub.
4. **Opening a source page**: when you open a saved page address from the library, your default browser connects to it.
5. **Checking for new versions**: with "Check for new versions automatically" on in Settings > About (the default), MyCapture checks once a day whether a new version exists. With it off, it checks only when you press **Check for updates**.
   - Microsoft Store installations check and install through the Microsoft Store.
   - Installations from the GitHub setup file or portable ZIP read the latest release information from the GitHub API (`api.github.com`). Pressing **Update** downloads the installer and its hash list from GitHub (`github.com`, `objects.githubusercontent.com`, `release-assets.githubusercontent.com`).
   - These requests carry only ordinary HTTP connection information (IP address and a User-Agent with the app name and version), never capture content or personal data. [GitHub's privacy statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement) applies to what reaches GitHub.

For Microsoft Store installations, installation and updates are provided by the Microsoft Store under the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## Deleting data

- You can delete library items in the app. New installations keep items with no time limit and clean up the oldest items outside folders only after they pass 1,000 items or 5 GB. Items marked Keep and items in folders are never cleaned up automatically.
- Installations updated from an earlier version keep their settings. The earlier defaults were cleanup of images older than 7 days, 300 items and 2 GB. Change the retention period and limits in Settings > Storage.
- You can clear the GitHub token in Settings.
- You can delete the downloaded translation model in Settings.
- Uninstalling the app deletes the settings and library in its package folder.

## Contact

Send privacy questions to [support@mimiloaf.com](mailto:support@mimiloaf.com) or through [issues](https://github.com/sukwoo0711-maker/mycapture-support/issues). Report security issues privately through [a security advisory](https://github.com/sukwoo0711-maker/mycapture-support/security/advisories/new) instead of a public issue.
