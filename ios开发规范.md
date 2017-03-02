# ios开发规范

## 1 前言
经过IOS开发团队的整理完善、技术委员会评审，ios开发规范现已正式发布，从即日起，IOS开发团队需遵从此规范进行项目及产品的开发。
## 2 关于命名
### 2.1 统一要求
##### ● 含义清楚，尽量做到不需要注释也能了解其作用，若做不到，就加注释
##### ● 使用全称，不使用缩写，尽量用英文命名
### 2.2 类的命名
##### [强制] 大驼峰式命名:每个单词的首字母都采用大写字母
示例：

```
HomePageViewController
```
##### [强制] 后缀要求：
 ViewController: 使用 ViewController 做后缀
 
 NavigationController：使用 NavigationController 做后缀
 
 TabBarController：使用 TabBarController 做后缀
 
 View: 使用 View 做后缀
 
 UITableCell：使用 Cell 做后缀
 
 Protocol: 使用 Delegate 或者 DataSource 作为后缀
 
 UI 控件依次类推
 
 示例：

```
HomeViewController
AlertView
NewsCell
UITableViewDelegate
nameLabel
```
### 2.3 私有变量
##### [强制] 小驼峰式命名:第一个单词以小写字母开始，后面的单词的首字母全部大写
示例：

```
firstName、lastName
```
##### [强制] 以 _ 开头，第一个单词首字母小写
示例：

```
NSString * _somePrivateVariable
```
##### [强制] 私有变量放在 .m 文件中声明
### 2.4 常量
##### [强制] 局部常量放在 .m 文件中，使用 static 和 const 共同修饰，常量名 头，后面的单词首字母大写，其余小写。(注意 const 修饰位置)
示例：

```
static NSTimeInterval const kAnimateDuration = 0.3;
static NSString * const kUserName = @"tangmin";
```
### 2.5 property 变量
##### [强制] 小驼峰式命名
示例：

```
@property (nonatomic, copy) NSString *loginName;
```
### 2.6 宏命名
##### [强制] 全部大写，单词间用 _ 分隔。(常量命名)
示例：

```
#define THIS_IS_AN_MACRO @"THIS_IS_AN_MACRO"
```
##### [强制] 以字母 k 开头，后面遵循大驼峰命名。(常量命名)
示例：

```
#define kWidth self.frame.size.width
```
##### [强制] 小驼峰命名。(带参数命名)
示例：

```
#define getImageUrl(url) [NSURL URLWithString:[NSString stringWithFormat:@"%@%@",kBaseUrl,url]]
```
### 2.7 Enum
##### [强制] Enum 类型的命名与类的命名规则一致
##### [强制] Enum 中枚举内容的命名需要以该 Enum 类型名称开头
示例：

``` ios
typedef NS_ENUM(NSInteger, AFNetworkReachabilityStatus) {
    AFNetworkReachabilityStatusUnknown = -1,    AFNetworkReachabilityStatusNotReachable = 0,
    AFNetworkReachabilityStatusReachableViaWWAN = 1,
    AFNetworkReachabilityStatusReachableViaWiFi = 2
};
```
### 2.8 Delegate 命名
##### [强制] 类的实例必须为回调方法的参数之一
```
- (NSInteger)tableView:(UITableView*)tableView numberOfRowsInSec tion:(NSInteger)section safd:(NSString *)string
```
##### [强制] 回调方法的参数只有类自己的情况，方法名要符合实际含义
```
- (NSInteger)numberOfSectionsInTableView:(UITableView*)tableView
```
##### [强制] 以类的名字开头(回调方法存在两个以上参数的情况)以表明此方法 是属于哪个类的
```
- (UITableViewCell*)tableView:(UITableView*)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
```
##### [强制] 使用 did 和 will 通知 Delegate 已经发生的变化或将要发生的变化
```
- (NSIndexPath*)tableView:(UITableView*)tableView willSelectRowAtI ndexPath:(NSIndexPath*)indexPath;- (void)tableView:(UITableView*)tableView didSelectRowAtIndexPath:( NSIndexPath*)indexPath;
```
## 3 私有方法及变量声明
### 3.1 声明位置
##### [强制] 在.m 文件中最上方，定义空的 category 进行声明
示例：

```#import "CodeStandardViewController.h"
// 在这个 category(类别)中定义变量和方法
@interface CodeStandardViewController ()
{
    // 声明私有变量
}
// 私有方法(可以不声明)
- (void)samplePrivateMethod;@end
@implementation CodeStandardViewController
// 私有方法的实现
- (void)samplePrivateMethod
{
    //some code
}
```
## 4 关于注释
最好的代码是不需要注释的，尽量通过合理的命名、良好的代码把含义表达清楚，在必要的地方添加注释，注释需要与代码同步更新，如果做不到命名尽量的见名知意的话，就可以适当的添加一些注释或者 mark。
### 4.1 属性注释
##### [强制] 在属性定义的前一行使用//进行注释说明
示例：

```
// 学生
@property (nonatomic, strong) Student *student;
```
### 4.2 方法声明注释
##### [强制] 在Xcode8以上使用快捷键command+option+/自动生成
示例：

```
/**
 登陆验证

 @param userName 用户
 @param password 密码
 @param complete 执行完毕的 block
 @return 
 */
+ (void)loginWithPersonId:(NSString *)personId password:(NSString *)password complete:(void (^)(CheckLogon *result))complete;
```
## 5 关于UI布局
##### [强制] 使用 Interface Builder 进行界面布局的时候，Xib 文件的命名与其对应的.h 文件保持相同，Xib 文件中控件的组织结构要合理，Xib 文件中控件需要有合理的可读性强的命名，方便他人理解。
## 6 格式化代码
### 6.1 指针 "*" 位置
##### [强制] 定义一个对象时，指针 "*" 靠近变量
示例：

```
NSString *userName;
```
### 6.2 方法的声明和定义
##### [强制] 在 - 、+ 和 返回值 之间留一个空格，方法名和第一个参数之间不留空格
示例：

```
- (id)initWithNibName:(NSString *)string nibNameOrNilbundle:(NSBundle *)nibBundleOrNil{
    //some code
}
```
### 6.3 方法的声明和定义
##### [强制] 使用 xcode 默认缩进，即 tab = 4 空格
##### [强制] 使用 xcode 中 re-indent 功能定期对代码格式进行整理
##### [强制] 相同类型变量声明需要独行声明
示例：

```
CGFloat oringX = frame.origin.x; 
CGFloat oringY = frame.origin.y; 
CGFloat lineWidth = frame.size.width;
```
##### [强制] Method 与 Method 之间空一行
示例：

```
- (void)samplePrivateMethod{...}
- (void)sampleForIf 7 
{...}
```
### 6.4 对 method 进行分组
##### [强制] 使用 #pragma mark - 方式对类的方法进行分组
分组命名参考:

\#pragma mark – life cycle 

\#pragma mark – Delegate 

\#pragma mark – CustomDelegate... 

\#pragma mark – event\#pragma mark - network 

\#pragma mark – private 

\#pragma mark – getter/setter
示例：

```
#pragma mark - private
- (void)samplePrivateMethod1{...}

- (void)samplePrivateMethod2{...}

- (void)samplePrivateMethod3{...}

#pragma mark - public
- (void)samplePublicMethodWithParam:(NSString*)sampleParam{...}

#pragma mark - life cycle
- (id)initWithNibName:(NSString *)nibNameOrNilbundle:(NSBundle *)nibBundleOrNil
{...}

- (void)viewDidLoad{...}

- (BOOL)shouldAutorotateToInterfaceOrientation:(UIInterfaceOrientation) interfaceOrientation{...}
```
### 6.5 大括号写法
##### [强制] 对于类的 method: 左括号另起一行写(遵循苹果官方文档)
示例：

```
- (id)initWithNibName:(NSString *)nibNameOrNilbundle:(NSBundle *)nibBundleOrNil{    self = [super initWithNibName:nibNameOrNil bundle:nibBundleOrNil];
    if (self) {
        // Custom initialization    }
    return self;
}
```
##### [强制] 对于其他使用场景: 左括号跟在第一行后边，左括号前留一个空格
示例：

```
- (void)sampleMethod
{
    BOOL boolCondition = YES;
    if(boolCondition) {
        // do something here    }
    int i = 0;
    while (i < 10) {
        // do something here
        i = i + 1;
    }
}
```
##### [强制] 任何需要写大括号的部分，不得省略
错误示例：

```
- (void)wrongExampleMethod
{
    BOOL boolCondition = YES;
    if (boolCondition)        NSLog(@"this is wrong!!!");
    while (someCondition)        NSLog(@"this is wrong!!!");
}
```



