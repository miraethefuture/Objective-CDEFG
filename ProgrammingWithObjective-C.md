

...

# Introduction
## Protocols Define Messasing Contracts
  
  Objective-C 앱 안에서 일어나는 대부분의 동작은 객체들이 서로에게 보내는 메세지의 결과로써 일어납니다.  
  이 메세지들은 보통 클래스 인터페이스에 작성된 메서드로부터 만들어집니다. 하지만 때때로는, 특정 클래스와 직접적으로 연결되어 있지 않고 서로 관련된 메서드들을 정의할 수 있는 것이 유용합니다.  
    
  Objective-C는 서로 관련된 메서드 그룹을 정의하기 위해 프로토콜을 사용합니다. 한 객체가 자신의 delegate에서 호출할 수도 있는 메서드들과 같은 것들이죠. 이 메서드들은 필수적일 수도, 그렇지 않을 수
  도 있습니다. 클래스들은 어떤 프로토콜을 따르는지 나타낼 수 있고, 프로토콜이 필수적으로 필요로하는 메서드들의 구현을 제공해야 합니다.
    
    
    
# Defining Classes


## The interface for a class Defines Expected Interactions  
  
  객체 지향 프로그래밍의 장점 중 하나는 바로, 클래스를 사용하기 위해 알아야 할 것은 클래스가 자신의 인스턴스와 상호작용하는 방식뿐이라는 것입니다. 더 자세히 말하자면, 객체는 내부 구현의 자세한 내용들을
  숨기도록 디자인되어야 한다는 것이죠. 만약 iOS 앱에서 표준 UIButton을 사용한다면, 우리는 픽셀들이 어떻게 버튼이 되어 화면에 나타나는지에 대해 알 필요는 없습니다. 우리는 버튼의 제목, 색깔과 같은
  속성들을 변경할 수 있고, 버튼이 화면에 올바르게 나타나 기대한 대로 동작하다는 것을 알기만 하면 됩니다.

  우리 자신의 클래스를 생성할 때, 이 public attributes(속성)와 behaviors에 대해 생각해 보는 것에서부터 시작해야 합니다. (숨겨진 내부 구현 부분이 아닌 공공적으로 사용되고 보일 부분)
  어떤 속성을 공공적으로 접근 가능하도록 하고 싶은가? 그 속성들이 변경될 수 있도록 해야 하는가? 다른 객체들이 우리가 만든 클래스의 인스턴스와 어떤 방식으로 소통할 수 있는가?에 대해 생각해 봐야 합니다.
  이런 정보들은 우리의 클래스의 interface 부분에 해당됩니다. 다른 객체들이 우리 클래스의 인스턴스와 어떤 방식으로 상호작용하도록 할지 그 방법을 정의하는 부분이죠.

### Basic Syntax  
  
  클래스 인터페이스를 선언하는 Objective-C 문법
  
  ```objective-c 
  @interface SimpleClass : NSObject
  
  @end
  ```


# Values and Collections
  
  ```objective-c
  @interface XYZCalculator : NSObject
  @property double currentValue;
  @end 
  ```
  
## C Structures Can Hold Primitive Values

  Cocoa, Cocoa Touch API 중 어떤 것은 값을 담기 위해 C Structures를 사용합니다. 한 예시로,
  ```objective-c 
  NSString *mainString = @"This is a long string";
  NSRange substringRange = [mainString rangeOfString:@"long"];
  ```
  NSRange 스트럭쳐는 위치와 길이에 대한 정보를 가집니다. 위 예시의 substringRange는 {10, 4} 라는 range를 가집니다. long 의 첫글자인 l 의 인덱스가 (mainString 에서) 10 이고 long의 길이가 4이기 때문이죠. {위치, 길이}
  
## Objects Can Represent Primitive Values 
  
### Strings Are Represented by Instrances of the NSString Class 
  
  ```objective-c 
  // 1.
  NSString *firstString = [[NSString alloc]
  initWithCString:"Hello World!"
  
  encoding:NSUTFStringEncoding];
 
  // 2.
  NSString *secondString = [NSString stringWithCString: "Hello World!"
  
  encoding:NSUTFStringEncoding];
  
  // 3.
  NSString *thirdString = @"Hello World!";
  ```
  위의 예시 코드는 모두 같은 일을 효과적으로 수행합니다. 주어진 문자를 보여주는 스트링 객체를 생성하죠.
