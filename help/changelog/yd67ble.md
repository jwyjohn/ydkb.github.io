# YD67BLE 固件更新记录
「+」新增， 「-」删除， 「^」升级,  「#」修复,  『 』重要

此处仅为更新日志记录，方便参考。下载固件请至ydkb.io，选择对应的键盘。

关于YD67BLE的更多说明，可参看：[yd67ble](keyboards/yd67ble.md)

##### 2023-06-11 (DN6B)
- 「^」降低Lock Mode下的耗电。先前的固件Lock Mode比起非Lock Mode的二级节能时耗电高出一倍多。

##### 2023-05-03 (DN53)
- 「^」从二级节能(包括Lock Mode)恢复时，依然保持当前的一级节能开关状态。

##### 2023-02-03 (DN23)
- 『# 』修复: DN1N固件，因为typo导致v1.0的PCB有部分按键无反应。

##### 2023-01-23 (DN1N)
- 「+」防止轴脚与地短路时，同时触发大量按键。
- 「^」主控与蓝牙模块之间的通讯，增加两重保险，提升可靠性。
- 「^」1: 每次主控传输命令到蓝牙前，检查之前的命令是否已经完成。
- 「^」2: 按键抬起时，会在发送后确认命令是否成功。如未成功会在下次循环再发，直至确认发送成功。

这次的蓝牙更新后，键盘这端应该不会出现按键后未弹起的情况了。

如果还遇到卡键按键未弹起现象，有可能是蓝牙命令由键盘发送后到电脑接收，这个过程中出了问题。

##### 2023-01-22 (DN1M) 
-   『# 』修复因为多打了一个数，造成上个固件最终上传的版本无法启动的问题。

##### 2023-01-20 (DN1K) 
-   「+」引入可调的防抖时间。目前只是预设了两种，NKRO按下防抖时间1ms，6KRO暂时预设是5ms。后续再加入可自定义设置。注意每次键盘重启后默认是NKRO模式，就又会回到1ms。万一部分轴体连击的可尝试临时切换到6KRO看是否有改善。
-   「+」 在可打字的地方按 <kbd>LShift+RShift+N</kbd>时，会打出数字0或6，0代表当前切换到了NKRO全键无冲模式，6代表切换到了6KRO任意6键无冲模式。
-   「+」增加 优先层 功能。使用瞬时开启的层，临时也被设为优先层，如果此层上有设置按键，则优先响应它，其次才根据所有的层状态从高往低查找。
-   「^」层的逻辑有些变化，把瞬间切换层和其他切换层分开来。现在逻辑上操作更直觉。

它不会破坏以往逻辑，但配合新逻辑，符合更多人对于层切换的期望。具体参看文档里关于层逻辑的新说明。

##### 2023-01-07 (DN17) 
- 「#」从Lock Mode等唤醒时，添加一个延迟，以解决少部分用户遇到的唤醒后键盘未正常工作的问题。

##### 2023-01-01 (DN11) 
- 「^」从这个固件开始，USB模式下默认开启NKRO全键无冲，蓝牙模式下依然是6KRO。现在应该很少人使用极老的系统不支持NKRO的了。

##### 2022-11-29 (DMBT) 
- 「#」修复问题：v1.0的版本 **按键 | 瞬时开启层** 未正常工作。

##### 2022-06-08 (DM68) 
- 「#」修复问题：最新macOS下(截止当前是12.4)，键盘进入节能时电量未正确刷新，导致系统无显示。

##### 2022-05-29 (DM5T) 
- 「+」二合一按键功能，增加 LT (P)。具体说明见: [按键 | 瞬时开启层](/edit-keymap/layer-tap-key.md)

##### 2022-05-08 (DM58) 
- 「^」改进，休眠唤醒后，默认连接可能非USB的问题。原因是有的主板或系统启动后识别USB需要更长时间。
- 「+」USB连接时，电脑休眠后，支持用键盘唤醒电脑。

##### 2022-04-22 (DM4M) 
-   『^』提升两个蓝牙设备间切换时的准确率。

##### 2022-04-13 (DM4D) 
-   『#』修复一个bug：当插着USB线时，切换到使用蓝牙，这时再拔掉USB线。此时在蓝牙连接下，键盘有可能不会再进入节能模式。

##### 2022-03-20 (DM3K) 
- 『+』按键防抖升级为疾速防抖，最快可以在按下按键后0.1ms内触发。
- 「^」改进Lock Mode按键，增加防抖优化。需要F和J按下稳定且其他按键也无任何抖动时，才能退出Lock Mode。
- 『-』取消YD67BLE v1.0的选项，完善了该单独固件支持多个版本。


##### 2022-02-27 (DM2R)
- 『+』修饰键组合键的一点点增强，方便实现类似<kbd>Ctrl+H J K L</kbd>或<kbd>Ctrl+N B P F</kbd>为方向键的操作，具体见说明 [修饰键组合键](edit-keymap/mods-key.md)
- 「^」 节能模式下的watchdog逻辑稍微改进了一下。
- 「+」使用 <kbd>LShift+RShift+LCtrl+B</kbd>组合可以直接进入刷机模式。


##### 2021-09-24 (DL9O)
- 「+」 键盘启动时增加一个版本指示，对于1.0或1.01版（按键矩阵使用74HC595的版本），caps指示灯会快闪三下。
- 「+」设置为 Tap二合一按键，如果其中是CapsLock，增加一个100ms的延时，让它在MacOS下可以正常切换大小写。
- 「^」 提高 [Esc 与 \`\~](/features/tricky-esc) 功能在单独按触发 Esc 时的响应速度。

