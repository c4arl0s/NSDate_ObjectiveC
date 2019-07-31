# NSDate_ObjectiveC

NSDate_ObjectiveC

Date objects are immutable, representing an invariant time interval relative to an absolute reference date (00:00:00 UTC on 1 January 2001).

To get the current date 

``` objective-c
NSDate *date = [NSDate date];
NSLog(@"Today is %@", date);
```

``` console
2019-07-29 22:44:19.938725-0500 NSDate_Project[2349:32571] Today is Mon Jul 29 22:44:19 2019
```


```objective-c
//
//  main.m
//  DateListPrintAllObjects
//
//  Created by Carlos Santiago Cruz on 4/19/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

#import <Foundation/Foundation.h>

int main(int argc, const char * argv[]) {
    @autoreleasepool {
     
        // Create three NSDate objects
        NSDate *now = [NSDate date];
        NSDate *tomorrow = [now dateByAddingTimeInterval:24*60*60];
        NSDate *yesterday = [now dateByAddingTimeInterval:-24*60*60];
        
        // Create an array containing all three  (nil terminates the list)
        NSArray *dateList = [NSArray arrayWithObjects:now, tomorrow, yesterday, nil];
        
        NSUInteger dateCount = [dateList count];
        
        for(int i=0; i<dateCount; i++ ) {
            NSDate *d = [dateList objectAtIndex:i];
            NSLog(@"Here is a date: %@", d);
        }
    }
    return 0;
}
```

``` console
2019-07-29 22:36:22.577631-0500 DateListPrintAllObjects[1965:25343] Here is a date: Mon Jul 29 22:36:22 2019
2019-07-29 22:36:22.577769-0500 DateListPrintAllObjects[1965:25343] Here is a date: Tue Jul 30 22:36:22 2019
2019-07-29 22:36:22.577808-0500 DateListPrintAllObjects[1965:25343] Here is a date: Sun Jul 28 22:36:22 2019
Program ended with exit code: 0
```

# Simple use of NSDate and UIDatePicker

``` objective-c
//
//  ViewController.m
//  NSDateAndPicker
//
//  Created by Carlos Santiago Cruz on 7/30/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

#import "ViewController.h"

@interface ViewController ()
@property (weak, nonatomic) IBOutlet UIDatePicker *datePicker;

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    NSDate *now = [NSDate date];
    [self.datePicker setDate:now animated:NO];
    NSLog(@"now is : %@", now);
}


@end
```

![Screen Shot 2019-07-30 at 9 49 59 PM](https://user-images.githubusercontent.com/24994818/62180013-171cec00-b314-11e9-94e1-0e09d5a5980f.png)

# Implementing an Action

``` objective-c
//
//  ViewController.m
//  NSDateAndPicker
//
//  Created by Carlos Santiago Cruz on 7/30/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

#import "ViewController.h"

@interface ViewController ()
@property (weak, nonatomic) IBOutlet UIDatePicker *datePicker;

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    
    NSDate *now = [NSDate date];
    [self.datePicker setDate:now animated:NO];
    NSLog(@"now is : %@", now);
}
- (IBAction)didChangePicker:(id)sender {
    NSDate *selectedDate = [self.datePicker date];
    NSString *message = [[NSString alloc] initWithFormat:@"The date and time you selected is: %@", selectedDate];
    UIAlertController *alert = [UIAlertController alertControllerWithTitle:@"Date and time selected"
                                                                   message:message
                                                            preferredStyle:UIAlertControllerStyleAlert];
    UIAlertAction *oKButton = [UIAlertAction actionWithTitle:@"OK"
                                                       style:UIAlertActionStyleDefault
                                                     handler:nil];
    [alert addAction:oKButton];
    [self presentViewController:alert animated:YES completion:nil];
    
    
}


@end
```

![Screen Shot 2019-07-30 at 10 10 45 PM](https://user-images.githubusercontent.com/24994818/62180847-f4400700-b316-11e9-8499-71b994e1403e.png)





