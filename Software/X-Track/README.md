# X-TRACK 更新日志
> https://github.com/FASTSHIFT/X-TRACK

## [v0.1] - 2021-3-21
* 1.框架搭建完成，全新MVP(Model-View-Presenter)架构
* 2.更新3D Model，门板完美安装
* 3.修复串口缓冲队列过载导致GPS解析连续失败的BUG
* 4.添加长按开机功能
* 5.添加计步显示
* 6.速度显示使用kph为单位
* 7.添加新的ButtonEvent库
* 8.添加Filters数字滤波器库 
* 9.添加新的TonePlayer库
* 10.格式化LIS3DMDL库的代码
* 11.格式化LISM6DSM库的代码
* 12.添加新的简易表盘页面
* 13.为LiveMap页面添加group，优化Encoder交互
* 14.LiveMap已可以正常显示航向，使用GPS的航向信息
* 15.重新校准MapConv地图坐标
* 16.添加HAL_AHRS姿态解算
* 17.添加HAL_Encoder接口
* 18.添加HAL_GPS串口透传，可使用上位机对GPS模块进行配置
* 19.添加GNSSToolKit_Lite配置工程
* 20.添加lv_get_indev()
* 21.添加__wfi()，可能省点电

## [v0.2] - 2021-4-19
* 1.添加ArtDesign工程，使用Adobe Illustrator
* 2.添加异步无锁Buffer库：PingPongBuffer
* 3.删除离线图片和字体转换工具
* 4.修改页面ID格式：DialplatePage->Pages/Dialplate
* 5.添加消息发布订阅框架：DataCenter
* 6.将HAL.h转移至应用层
* 7.HAL: Clock_GetValue->Clock_GetInfo
* 8.在PC模拟器上使用PC的电量显示
* 9.更新PageManager
* 10.降低SD热插拔监控扫描速度
* 11.删除Music_Astronomia
* 12.在编码器按下时忽略滚动，减少误触
* 13.更新Dialplate页面
* 14.更新LiveMap页面

## [v0.3] - 2021-5-12
* 1.lvgl迁移至v8.0.0
* 2.PingPongBuffer转移至App/Utils/DataCenter，以提供无锁的线程安全的数据块访问，添加volatile关键字
* 3.VS工程在Debug下启用AddressSanitizer，捕获异常的内存操作
* 4.Heap和Stack调整
* 5.更新ButtonEvent库
* 6.更换新的文件系统接口lv_fs_if
* 7.系统配置文件SysConfig.h -> Config.h
* 8.Utils添加WString for PC
* 9.ResourceManager更新，使用std::vector作为资源池
* 10.PageManager更新，lvgl-v8适配，简化子模块命名，使用std::vector作为页面池，使用std::stack作为页面栈
* 11.地图坐标转换器MapConv更新，但未找到更精确的地图坐标换算算法
* 12.去除lv_theme_custom
* 13.添加GPX库，将来用于生成GPX格式的标准轨迹记录文件
* 14.使用C++ template重写Filters滤波器合集库
* 15.数据发布订阅处理中心DataCenter更新，添加错误码、通知、数据提交等功能
* 16.StatusBar更新，添加背景色柔和渐变、电池充电等特效
* 17.LiveMap页面更新，新的滚动条和info按钮
* 18.Dialplate页面更新，操作按钮已可以使用
* 19.数据处理节点DP_SportStatus更新，更新卡路里换算算法、距离、速度滤波等处理方法
* 20.添加新的数据处理节点DP_Recorder，用于记录轨迹于SD卡中
* 21.电池AD采样使用中断模式，而不使用DMA
* 22.文件系统SD对象不再全局共享
* 23.屏蔽开机启动时Encoder按键事件

## [v0.4] - 2021-5-16
* 1.lvgl更新
* 2.支持导出GPX格式的轨迹记录文件，推荐使用[GPXSee](https://github.com/tumic0/GPXSee)查看轨迹
* 3.Clock_info_t结构体成员单词全拼
* 4.LiveMap页面更新，改进的操作方式与显示特效
* 5.去除MAP数据映射宏，使用lv_map替代
* 6.SD支持时间戳记录，支持自动检测和创建缺失的文件夹

## [v0.5] - 2021-5-23
* 1.添加SystemInfos页面
* 2.添加IMU和地磁MAG数据处理节点
* 3.修改轨迹记录默认文件名
* 4.规范lv_event成员参数获取方式
* 5.修复DataCenter缓冲区读取释放BUG
* 6.添加Version.h存放版本信息
* 7.HAL::GPS_Info_t添加hour_utc成员

## [v0.6] - 2021-5-31
* 1.更新lvgl
* 2.添加App_Uninit()，绑定关机事件
* 3.添加DP_LIST.inc，更优雅的数据处理节点注册方式
* 4.添加IMU/MAG_Commit，向数据中心提交数据
* 5.添加StorageService数据储存服务，使用JSON格式储存数据
* 6.添加ArduinoJson解析库
* 7.运动数据处理节点 sportStatusInfo -> sportStatus，添加储存绑定
* 8.去除HAL::AHRS
* 9.GPS在未定位成功时，经纬度海拔统一置零
* 10.HAL::Power添加关机事件回调
* 11.CONTROLLER -> PRESENTER
* 12.添加StartUp页面，展示开机动画
* 13.LiveMap地图页面，在未定位成功时的默认位置为天安门
* 14.StatusBar状态栏，函数AppearAnimStart -> Appear 
* 15.解决SystemInfos页面在自动管理Cache时退出页面造成的Crash
* 16.修复MAG数据显示的bug
* 17.DataCenter添加主账户AccountMain，自动订阅所有的子节点，用于发送通知
* 18.PageManager在删除root时需要使用异步删除lv_obj_del_async()，在root动画生命周期结束后删除
* 19.降低GPS和Sensor的数据更新频率，分别为5Hz和1Hz

## [v0.7] - 2021-6-5
* 1.更新拆分STL模型文件
* 2.TonePlayer转移至App/Utils
* 3.在关机时自动保存正在记录的轨迹文件
* 4.优化轨迹记录操作体验
* 5.DataCenter合并定时器回调到AccountEvent
* 6.AccountEvent添加Account* 参数
* 7.添加DATA_PROC_INIT_DEF节点定义
* 8.添加StatusBar状态栏、MusicPlayer播放器、TzConv时区转换器数据节点
* 9.优化电池电量滤波算法 Hysteresis + MedianQueue
* 10.转移STORAGE_VALUE_REG宏定义至DataProc_Def.h
* 11.在SD插入时自动加载JSON系统配置文件
* 12.添加Common/Music
* 13.优化DataCenter和PageManager日志输出等级
* 14.优化GPX库
* 15.优化PAGE_STASH_POP
* 16.去除PageManager::Pop函数的stash参数
* 17.添加Arduino Time时间转换库
* 18.去除GPS_Info_t的hour_utc成员，使用TzConv进行时区转换

## [v0.8] - 2021-6-15
* 1.格式化所有代码
* 2.APP_Init添加ACCOUNT_SEND_CMD，简化Account通知调用
* 3.dataCenter("Bilibili") -> dataCenter("CENTER")
* 4.添加SysConfig节点，用于保存系统设置
* 5.Power节点使用Account通知方式调用MusicPlayer，而不使用HAL::Audio_PlayMusic
* 6.去除HAL::Backlight_UpdateBKP()和Backlight_GetBKP()
* 7.DialplateModel添加节点名称验证
* 8.LiveMapModel添加节点名称验证
* 9.DataCenter添加Account双buffer动态内存申请检查
* 10.Account::GetPublisherLen() -> GetPublisherSize(), GetSubscribeLen() -> GetSubscribeSize()
* 11.更新lv_anim_timeline，支持设置progress，已提交至lvgl主线
* 12.去除lv_obj_ext_func不常用的函数
* 13.StorageService扩大JSON_BUFFER_SIZE 256 -> 512, 添加字符串类型参数读取返回值检查
* 14.添加硬件定时器配置到Config.h
* 15.修改版权声明遗留拼写错误

## [v0.9] - 2021-6-24
* 1.更新ButtonEvent，支持EVENT_LONG_PRESSED_RELEASED
* 2.调整lvgl内存池，32KB -> 64KB
* 3.HAL_GPS支持读取csv格式的文件，在PC上模拟位置变化
* 4.更新LiveMap页面，支持实时绘制运动轨迹，支持自适应分辨率动态加载地图
* 5.更新StartUp页面，移除默认样式，并在开机动画过程中屏蔽Encoder事件
* 6.修复SystemInfos页面因为忘记释放style.focus导致的内存泄漏
* 7.优化DataCenter的Account的cache申请失败判断逻辑
* 8.添加lv_allocator，使用lvgl接管std::vector内存管理实现
* 9.更新MapConv，MapKeyRootName -> MapFilePath，ConvertMapTile() -> ConvertPosToTile()
* 10.添加TileConv，通用的瓦片动态加载算法实现
* 11.添加TrackFilter轨迹过滤器，包含TrackPointFilter曲线关键点提取算法和TrackLineFilter曲线区域裁剪算法
* 12.HAL::Encoder添加Encoder_SetEnable()方法

## [v1.0] - 2021-7-1
* 1.更新lvgl v8.1.0 dev
* 2.添加TrackFilter数据处理节点，储存过滤后的拐点坐标
* 3.优化DP_Clock RTC自动校准
* 4.优化DP_GPS提示音播放，添加cache，使用Publish向订阅者推送数据，减少定时轮询拉取
* 5.添加GPX_Parser，支持直接解析GPX数据还原轨迹
* 6.Config.h转移到App
* 7.页面添加namespace Page命名空间
* 8.优化LiveMap轨迹显示，在轨迹记录时显示轨迹，使用lambda表达式替换部分回调函数
* 9.优化StatusBar充电动画
* 10.DataCenter添加注释
* 11.PageManager添加注释
* 12.lv_allocater添加遗漏的运算符重载
* 13.添加Utils/Stream，来自Arduino
* 14.转移CommmonMacro.h到HAL，去除Basic文件夹

## [v1.1] - 2021-7-7
* 1.支持在GPX中记录海拔和时间，可在GPXSee查看爬升和速度统计
* 2.更新StartUp页面，使用匿名函数回调
* 3.更新SystemInfos页面，添加Author署名和Build时间，电池状态 State -> Status
* 4.更新lvgl
* 5.更新GPX生成库，添加遗漏的time_成员
* 6.尝试将lvgl部分函数放在RAM中执行，但是执行速度提升不明显

## [v1.2] - 2021-7-11
* 1.添加StackInfo库，支持在裸机环境下测量栈使用情况
* 2.Stack_Size 0x2500 -> 0x1000
* 3.更新DP_Storage数据储存节点，支持拉取储存器使用情况
* 4.更新Config.h，添加显示器分辨率和缓冲区配置
* 5.添加触控逻辑
* 6.修复StatusBar充电动画闪烁的BUG，添加SD卡图标
* 7.SystemInfos页面添加SD卡状态监测显示

## [v1.3] - 2021-7-18
* 1.Config.h添加传感器使能配置选项
* 2.DataCenter添加cache自动初始化置0
* 3.添加Microsoft官方TileSystem解析库，供mapConv调用
