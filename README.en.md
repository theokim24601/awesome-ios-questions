# Awesome iOS Questions

iOS & Mobile 개발을 하면서 떠올랐던 질문과 의견들에 대해 기록하고 있습니다.

면접 만을 위해서가 아니라 iOS 개발을 할 때 한 번쯤은 고민해 봐야 할, 고민해 봤으면 하는 점들을 기록하고 있습니다. 단순히 정의를 묻는 것뿐만 아니라 구체적인 상황을 제시하여 문제 해결 전략을 배우고 깊이 있는 질문을 통해 인사이트를 넓히는 것이 주 목적입니다.

PR은 언제든 환영입니다. 🤩

*Read this in other languages: [English](README.md), [한국어](README.ko.md)*

## App

- Assuming you have an app with millions of users, what steps can you take to minimize bugs or regressions from occurring in old versions?
- How do you prioritize fixing a crash? Is a smaller crash in a more frequently used part of the app more important to fix than a larger crash in a less frequently used part?
- 세 개의 Endpoint[Dev, Stage, Prod]가 있고 세 Endpoint를 오가며 모바일 앱을 테스트하려고 한다면, 어떤 방식으로 해결할 수 있나?
  - Build Configuration으로 해결할 수 있는지? 단점은?
  - 런타임에 해결할 수 있는 방법이 있는지?
- 오프라인(네트워크 연결이 안 된) 모드를 지원하는 앱이 있다. 사용자가 오프라인 상태에서 작업한 내용을 서버와 동기화하려면 어떻게 해야 하나?

## iOS

- NSCache와 Dictionary의 차이점이 무엇인가?
- Dictionary는 Thread-Safe 하지 않은데, 구체적으로 어떤 문제를 야기할 수 있나?
  - 두 군데에서 동시에 업데이트를 한다고 할 때 Consistency를 지키기 위한 방법은?
  - 다음 코드는 Thread-Safe한가?
    ```swift
    let queue = DispatchQueue(label: "awesome-ios-questions")
    var _dict: [Int] = []
    var dict: [Int] {
      get {
        return queue.sync { _dict }
      }
      set {
        queue.sync { _dict = newValue }
      }
    }
    ```
- Background Notification이 무엇인가?
  - Background Notification을 어떤 상황에 사용할 수 있을지 구체적인 예시 2가지만 떠올려보자면?
  - Background Notification은 제약사항이 많다. 알림 전달이 보장되지 않는데, 이를 대체할 수 있는 방법은 무엇일까?
- iOS에서 사용되는 디자인 패턴은 어떤 것이 있나?

### Concurrency

- Dispatch queue에 등록한 작업을 취소할 수 있나?

### UIKit

- UIViewController의 Life cycle 중에 `viewWillAppear`와 `viewDidAppear`가 있는데, 이 둘은 항상 짝으로 호출될까?
- What is the purpose of the reuseIdentifier? What is the advantage of setting it to a non-nil value?

### DeepLink

- 사파리에서 `https://ourdomain.com` 링크를 클릭했을 때 앱으로 연결해달라는 요구사항이 생겼다. 필요한 작업은 무엇인가?
  - Universal Links가 어떤 원리로 동작하는지 앱을 설치하는 시점부터 시간 흐름 순으로 설명할 수 있나?
  - Universal Links가 생겨난 이유와 한계는 무엇인가?

## Swift

- Value Type과 Reference Type에는 무엇이 있는가?
  - Collection, Closure는 무슨 타입인가?
- What is the difference optional between `nil` and `.none`?
- Generic이 필요한 이유는?
- What is the difference between Generics and Any?
- What is the difference between Array and NSArray?
- 아래 코드의 `print` 결과?
  ```swift
  var verb = "like"

  let closure = { [verb] in
    print("I \(verb) swift")
  }

  verb = "hate"

  closure()
  ```
- 클래스 안의 `static`함수와 `class`함수의 차이는 무엇인가?
- Why do we need to specify self to refer to a stored property or a method When writing asynchronous code?

### Memory

- 클로저에서 `[weak self]`는 어떤 상황에 쓰이는가?
  - `guard let self else { return }` 가 갖는 의미는 무엇인가?
  - `guard let self else { return }` 대신 `self?.`를 사용하면 어떻게 되나?
- 클로저가 실행되는 동안 self가 메모리에서 해제되지 않도록 보장할 수 있는 방법이 있는지?
- What is your process for tracing and fixing a memory leak?

### Performance

- `struct`와 `class`의 성능 차이가 발생하는 이유는?
- Collection의 `map()`, `redeuce()` 와 `for loops` 중에 어떤 것이 더 빠르고 무엇이 성능의 차이를 가져오는가?
- Array와 Dictionary 중 어떤 것이 탐색 속도가 더 빠른가?

## Reactive

### Combine


### Rx

- DisposeBag이 무엇이고 어떻게 동작하는가?
- `dispose()`를 호출하면 구독은 즉각 중단이 되는가?

## General

- What is difference between REST and GraphQL?

## License

**Awesome iOS Questions** is available under the MIT license. See the [LICENSE](LICENSE) for details.
