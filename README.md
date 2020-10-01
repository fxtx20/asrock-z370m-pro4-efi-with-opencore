# asrock-z370m-pro4-efi-with-opencore

Hackintosh EFI with OpenCore for AsRock z370m pro4

运行在华擎z370m pro4主板上的基于OpenCore的黑苹果EFI

## 配置

* 主板：华擎z370m pro4
* CPU：Intel i9 9900T es
* GPU：UHD630
* RAM：16GB 3200 MHZ DDR4
* ROM：1TB NVMe SSD
* 网卡：Fenvi-T919 BCM94360CD

## 是否驱动

* 声卡 √
* 显卡 √
* Wi-Fi √
* 蓝牙 √
* 接力 √
* 隔空投送 √
* 睡眠唤醒 √

## 注意事项

* 第一次使用注意在bootarg中添加-v参数用于跑日志，并且打开ShowPicker，展示启动项
* 注意重新生成机型信息 (用OpenCore Configurator)
* 开关相应的BIOS设置 (从下面参考链接中找对照表)
* 如果遇到问题自行搜索解决，注意，不要用百度，百度是搜不出正确答案来的
* 删除efi或者是kext，需要同步在config.plist中做相应修改，如果漏了会开不了机，到时候会报错，就需要进PE去手动改，那就很麻烦，所以修改的时候一定要注意！
* 如果你的CPU型号和我的不同，那么你还需要定制CPUFriendDataProvider.kext，具体方法到参考链接第一条中去找。

### 一些可能出现的问题

* 部分USB接口失效，如遇到此问题，删除USBPorts.kext、USBPower.kext，并导入USBInjectAll.kext，确认USB能够使用后，使用Hackintool定制USB，大概方法就是每个USB接口都插一下，Hackintool里面的列表项会绿，然后把没绿的删除掉，导出会给你一个USBPorts.kext，然后再替换回来，删掉USBInjectAll.kext，如果使用正常，可以再把USBPower.kext放回来。USBPower.kext是快充的，如果你修改了机型，那么需要打开这个里面的plist，把IOKitPersonalities下面的机型改成你正在使用的机型。这个快充在我这个主板上只有type c那个口是生效的。
* 显示器显示比例不正确，或发紫等现象。有两种解决方法，一种是用Hackintool生成补丁，还有一种是开启HiDPI。建议使用第二种方法，不过第二种方法有碰运气等成分在里面，也就是说，如果第二种方法没有解决问题等话，可以再尝试第一种方法。
* 唤醒后显示器不亮，需要开关显示器。可以尝试修改机型，也就是说，如果只有核显，就用Mac mini，如果只有独显，就用Mac Pro，如果是核显独显都有，就用iMac。

## 参考

* https://blog.xjn819.com/?p=543 （基本上遇到等问题都能在这里面找到）
* https://blog.daliansky.net/OpenCore-BootLoader.html 
* https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#starting-point 官方文档
* https://mackie100projects.altervista.org/opencore-configurator/ 推荐使用这个工具编辑config.plist