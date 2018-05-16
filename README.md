# Note
```code
//
//  ViewController.m
//  t
//
//  Created by LiuYanQi on 2018/5/15.
//  Copyright © 2018年 LiuYanQi. All rights reserved.
//

#import "ViewController.h"

struct Bar{
    char *x;
    int y;
};

struct test
{
    char* p_ch;
    int ix;
};

struct Bar funct(){
    struct Bar result;
    char *foo = malloc(sizeof(char) * 1024);
    snprintf(foo, 1024, "%s - %s\n", "foo", "bar");
    result.x = foo;
    result.y = 11;
    return result;
}

char * CSTR(int *inTextLength){
    char *foo = malloc(sizeof(char) * 1024);        /* buffer for 1024 chars */
    snprintf(foo, 1024, "%s - %s\n", "foo", "bar"); /* puts "foo - bar\n" in foo */
//    printf("%s", foo);                                    /* prints "foo - bar" */
    *inTextLength = 11;
    return foo;
}



@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
                                         /* frees mem from malloc */
    int inTextLength;
    
//    char *foo = CSTR(&inTextLength);
////    NSLog(@"%@",@(inTextLength));
////    NSString *s = [NSString stringWithUTF8String: foo];
////    free(foo);
//    NSString *s = [[NSString alloc] initWithBytesNoCopy:foo length:inTextLength encoding:NSUTF8StringEncoding freeWhenDone:NO];
//    
//    NSLog(@"%@",s);
    
//    struct Bar dunno = funct();
//    NSString *d = [[NSString alloc] initWithBytesNoCopy:dunno.x length:dunno.y encoding:NSUTF8StringEncoding freeWhenDone:YES];
//    NSLog(@"%@", d);
//    
    struct test *p_test;
    p_test = malloc(sizeof(struct test));
    p_test->p_ch = malloc(20);
    char *p_ch = malloc(20);
    snprintf(p_ch, 20, "%s - %s\n", "foo", "bar");
    strcpy(p_test->p_ch, p_ch);
    free(p_ch);
    p_ch = p_test->p_ch;
    NSString *s = [NSString stringWithUTF8String: p_ch];
    printf("p_test->p_ch:/t%s/n", p_test->p_ch);
    free(p_test->p_ch); //如果注释掉这行，p_ch值仍为“Hello!”
    free(p_test);
    printf("after free(p_test), p_ch:/t%s/n", p_ch);

}

- (void)viewDidAppear:(BOOL)animated{
    [super viewDidAppear:animated];
//    printf("%s", foo);
}

- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}


@end

```
