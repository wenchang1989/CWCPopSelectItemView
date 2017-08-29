# CWCPopSelectItemView
轻量级弹出下拉菜单控件

效果

! [image](https://github.com/wenchang1989/CWCPopSelectItemView/blob/master/2017-08-29%2017_29_46.gif?raw=true)


使用

- (void)showpopView:(UIView *)curentView popType:(CWCPopType)type{

    self.managerObject = [[CWCUtilitiPopSelectItemsView alloc] initWithSelectArr:[@[@"第一个",@"第二个",@"第三个"] mutableCopy]];
    
    self.managerObject.delegate = self;
    self.managerObject.popType = type;
    [self.managerObject presenFromeSelectView:curentView];
}

- (void)selectWithIndext:(NSInteger)index{

    NSArray *arr = @[@"第一个",@"第二个",@"第三个"];
    
    self.myLabel.text = arr[index];
    
}

- (void)curentViewDidDismiss{

    NSLog(@"就这么消失了===");
    
}

详细介绍

@protocol CWCUtilitiPopSelectItemsViewSelectDelegate <NSObject>

@optional
/**
 选择item的回调

 @param index 标记位
 */
- (void)selectWithIndext:(NSInteger)index;

/**
 视图移除后的回调
 */
- (void)curentViewDidDismiss;
@end

typedef NS_ENUM(NSInteger, CWCPopType)
{
    CWCType_Left,
    CWCType_Right,

};

@interface CWCUtilitiPopSelectItemsView : NSObject

/**
 初始化

 @param selectArr 可选数组

 @return 实例
 */
- (instancetype)initWithSelectArr:(NSMutableArray *)selectArr;

/**
 显示视图

 @param selectView 目标视图
 */
- (void)presenFromeSelectView:(UIView *)selectView;

/**
 移除视图
 */
- (void)dismissAction;

/**
 *  代理
 */
@property (nonatomic, weak) id <CWCUtilitiPopSelectItemsViewSelectDelegate> delegate;
/**
 *  视图底图
 */
@property (nonatomic, strong) UIView *managerView;
/**
 *  弹出原始位置
 */
@property (nonatomic, assign) CWCPopType popType;
