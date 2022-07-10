

...

# Introduction
## Protocols Define Messasing Contracts
  
  Objective-C 앱 안에서 일어나는 대부분의 동작은 객체들이 서로에게 보내는 메세지의 결과로써 일어납니다.  
  이 메세지들은 보통 클래스 인터페이스에 작성된 메서드로부터 만들어집니다. 하지만 때때로는, 특정 클래스와 직접적으로 연결되어 있지 않고 서로 관련된 메서드들을 졍의할 수 있는 것이 유용합니다.  
    
  Objective-C는 서로 관련된 메서드 그룹을 정의하기 위해 프로토콜을 사용합니다. 한 객체가 자신의 delegate에서 호출할 수도 있는 메서드들과 같은 것들이죠. 이 메서드들은 필수적일 수도, 그렇지 않을 수
  도 있습니다. 클래스들은 어떤 프로토콜을 따른느지 나타낼 수 있고, 프로토콜이 필수적으로 필요로하는 메서드들의 구현을 제공해야 합니다.
  
  
# Values and Collections
  
  ```objective-c
  @interface XYZCalculator : NSObject
  @property double currentValue;
  @end 
  ```
  
