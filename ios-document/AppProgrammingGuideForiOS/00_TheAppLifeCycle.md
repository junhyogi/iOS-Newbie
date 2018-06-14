App Programming Guide for iOS - The App Life Cycle
===
[App Programming Guide for iOS - The App Life Cycle](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html)

The App Life Cycle
---

### The Main function

* 모든 C-based 앱과 동일하게 `main` function이 entry point. 단 직접 `main`을 작성하진 않고 Xcode에서 기본적으로 프로젝트의 일부로 만들어 줌
* UIKit framework에 제어 권한을 넘기는 일을 하고 끝.
  * App의 core object를 만듦
  * storyboard files를 기반으로 app의 user interface를 loading
  * 사용자 정의 코드를 호출하여 초기 설정 
  * App 의 run loop 실행
* 스토리 보드 파일과 custom initialize code만 내가 잘 적어주면 된다
```objectivec
#import <UIKit/UIKit.h>
#import "AppDelegate.h"
 
int main(int argc, char * argv[])
{
    @autoreleasepool {
        return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
    }
}
```

### The Structure of an App
* App의 Heart. [UIApplication](https://developer.apple.com/documentation/uikit/uiapplication) object
* UIApplication의 임무는 App과 System간의 interaction을 돕는다.
* iOS App은 MVC(Model-View-Controller)를 사용한다.
  * 앱의 데이터, 비지니스 로직, Visual을 구분한다.
  * 이는 화면 크기가 다른 여러 장치에서 실행할 앱을 만들 때 중요하다.

![Key objects in an iOS app](https://github.com/junhyogi/iOS-Document/blob/master/document/AppProgrammingGuideForiOS/images/figure_2_1.png)

* UIApplication
  * Event loop manage, High-level app behaviors
  * 앱의 주요 전환(transition) 혹은 push같은 특별한 event를 Delegate로 전달한다.
  * 웬만하면 상속하지 마라
* AppDelegate 
  * Custom code (init) 의 중심!
  * UIApplication 객체와 함께 작동하며 app 초기화, 상태 전환 등의 하이레벨 app event 처리
  * App에 존재하는 유일한 객체임을 보장한다. (따라서 앱의 초기 데이터 구조를 설정하는데 사용된다)
* Document, Data model
  * 앱의 컨텐츠 (데이터, 이미지 등..?) store
  * UIDocument를 상속해서 Data model object를 다룰 수 있다.
  * 자세한건 Document-Based App Programming Guide for iOS.
* View Controller
  * 하위 뷰들을 관리
  * App window에 뷰들을 보여줄 수 있도록 Setup 해준다
  * 뷰 로딩, 뷰 Presenting, Rotating에 대한 응답 등 처리
  * 자세한건 View Controller Programming Guide for iOS.
* UIWindow
  * 뷰가 screen에 보여지기 위한 조정 역할을 도맡아 함
   (coordinates the presentation of views)
  * 뷰의 컨텐츠가 변경되면 View controller를 통해 뷰를 업데이트 하고,
  * 윈도우를 갱신하거나 하진 않는다
  * 뷰를 hosting하는것 외에, UIApplication과 함께 event를 View나 VC에 전달하는 역할도 한다
* View, Control, Layer
  * View : 직사각형 영역에 컨텐츠를 그리고, 해당 영역의 이벤트에 응답하는 객체
  * Control : 버튼, Text field, Toggle switch 같은 특수 View
  * Layer는 컨텐츠를 visualization하는데 사용되고, View는 layer를 통해 컨텐츠를 렌더링 한다. 따라서 커스텀 레이어를 추가함으로써 복잡한 애니매이션이나 다양한 visual effect를 구현할 수 있다. 
