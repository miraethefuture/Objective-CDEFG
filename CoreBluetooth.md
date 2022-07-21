

# 오브젝트 씨, 블루투스 상태 확인해보기 

  간단하게 블루투스가 켜져있는지, 꺼져있는지 상태를 알아보는 코드를 정리해봅니다. 
  
  먼저 ViewController.h 에 작성한 코드 
  
  
  ```objective-c
  // ViewController.h
  
  
  #import <UIKit/UIKit.h>
  #import <CoreBluetooth/CoreBluetooth.h>
  
  
  @interface ViewController : UIViewController
  
  @property (nonatomic, strong) CBCentralManager *bluetoothManager;
  
  
  - (void)centralManagerDidUpdateState:(CBCentralManager *)central;
  
  @end

  ```
 
 
  그 다음은 ViewController.m 에 작성한 코드 
 
 
  ```objective-c
  // ViewController.m
  
  
  #import "ViewController.h"
  
  
  @interface ViewController ()

  @end
  
  
  @implementation ViewController
  
  - (void)viewDidLoad {
    [super viewDidLoad];
    
    
    if(!self.bluetoothManager)
    {
        NSDictionary *options = @{CBCentralManagerOptionShowPowerAlertKey: @NO};
        self.bluetoothManager = [[CBCentralManager alloc] initWithDelegate:self queue:nil options:options];
    }
  }
  


  - (void)centralManagerDidUpdateState:(CBCentralManager *)central
  {
      NSString *stateString = nil;


      switch(self.bluetoothManager.state)
      {
          case CBCentralManagerStateResetting: stateString = @"The connection with the system service was momentarily lost, update imminent."; break;
          case CBCentralManagerStateUnsupported: stateString = @"The platform doesn't support Bluetooth Low Energy."; break;
          case CBCentralManagerStateUnauthorized: stateString = @"The app is not authorized to use Bluetooth Low Energy."; break;
          case CBCentralManagerStatePoweredOff: stateString = @"Bluetooth is currently powered off."; break;

          case CBCentralManagerStatePoweredOn: stateString = @"Bluetooth is currently powered on and available to use."; break;

          default: stateString = @"State unknown, update imminent."; break;
      }

      NSLog(stateString); 
      // -> 로그에서 상태 메시지로 블루투스 연결 확인 가능 "Bluetooth is currently powered off." 이런 식으로 위 상태마다 출력되는 메시지를 로그에서 블루투스를 껐다 킬때마다 확인 할 수 있음
  }
  @end
  
  
  ```
  
