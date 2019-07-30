# NSDate_ObjectiveC

NSDate_ObjectiveC

Date objects are immutable, representing an invariant time interval relative to an absolute reference date (00:00:00 UTC on 1 January 2001).

To get the current date 

``` objective-c
NSDate *date = [NSDate date]
NSLog(@"Today is %@", date);
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




