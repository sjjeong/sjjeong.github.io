---
title: "iOS Firebase 셋팅"
date: 2019-12-08 02:10:00 +0900
categories:
- ios
- firebase
tag:
- ios
- swift
- firebase
---

# iOS 프로젝트에 Firebase project 추가하기


## 1. 앱 등록
![image](/assets/posts/2019-12-08/add_firebase_project_01.png)

기존 Firebase project에서 iOS 앱을 추가하면 위 그림과 같은 화면이 나오게 됩니다.  
여기서 `iOS 번들 ID`를 추가해줘야 하는데 xcode에서 프로젝트를 만들 때 입력 했던 Bundle Identifier를 입력해주면 됩니다.

![image](/assets/posts/2019-12-08/add_ios_project.png)

저는 이렇게 `com.dino.FirebaseStudySample`라고 Bundle Identifier를 만들었습니다.

![image](/assets/posts/2019-12-08/add_firebase_project_02.png)

`앱 등록`에서 `iOS 번들 ID`에 본인이 프로젝트의 `Bundle Identifier`를 추가하고 `앱 등록` 버튼을 눌러줍니다.

## 2. 구성 파일 다운로드
![image](/assets/posts/2019-12-08/add_firebase_project_03.png)

그림에서 보는 것 처럼 `GoogleService-Info.plist 다운로드`를 눌러 파일을 다운 받습니다.

![image](/assets/posts/2019-12-08/add_firebase_project_04.png)

다운 받은 파일은 그림처럼 프로젝트의 루트에 추가해 줍니다.

## 3. Firebase SDK 추가
![image](/assets/posts/2019-12-08/add_firebase_project_05.png)

terminal을 열고 프로젝트의 루트 경로까지 이동을 합니다.
> terminal에서 directory 이동은 `cd` 명령어를 사용합니다.

![image](/assets/posts/2019-12-08/add_firebase_project_06.png)

이동하고 나서 `pod init`라고 명령어를 실행하고 `ls`명령어로 확인해보면 `Podfile`이 추가 된 것을 확인 할 수 있습니다.
> 만약 pod 명령어가 없다면 [pod 명령어 설치 방법](https://stackoverflow.com/questions/20755044/how-to-install-cocoapods)을 따라하면 됩니다.

![image](/assets/posts/2019-12-08/add_firebase_project_07.png)

`open PodFile`명령어를 실행하면 Podfile를 편집할 수 있는 `텍스트 편집기` 앱이 실행 됩니다.  
파일 내부에 `pod 'Firebase/Analytics'`를 추가하고 저장을 합니다.

![image](/assets/posts/2019-12-08/add_firebase_project_08.png)

그 다음에 `pod install` 명령어를 실행 합니다.

![image](/assets/posts/2019-12-08/add_firebase_project_09.png)

install에 성공했다면 위 그림처럼 나오게 됩니다.

## 4. 초기화 코드 추가
![image](/assets/posts/2019-12-08/add_firebase_project_10.png)

`AppDelegate` 클래스를 열고  
```swift
import Firebase
```
Firebase를 import 한 다음에  
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
    // Override point for customization after application launch.
    FirebaseApp.configure()
    return true
}
```
FirebaseApp.configure() 코드를 추가해줍니다.

> 만약 `import Firebase`에서 `Could not build Objective-C module 'Firebase'`에러가 발생한다면 [firebase import 에러 수정 방법](https://stackoverflow.com/questions/48727206/firebase-cocoapods-error-message-could-not-build-objective-c-module-firebase/48728282)을 따라하면 됩니다.

## 5. 앱을 실행하여 설치 확인

![image](/assets/posts/2019-12-08/add_firebase_project_11.png)
![image](/assets/posts/2019-12-08/add_firebase_project_12.png)

Run을 해서 앱을 실행하고 Google 서버와 통신을 성공하면 위 그림처럼 `앱에 Firebase를 추가했습니다.` 메시지가 나오게 됩니다.


