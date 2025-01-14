# BLE40/BLUP 固件更新记录
「+」新增， 「-」删除， 「^」升级,  「#」修复,  『 』重要

此处仅为更新日志记录，方便参考。下载固件请至ydkb.io，选择对应的键盘。

##### 2023-05-03 (DN53)
- 「^」从二级节能(包括Lock Mode)恢复时，依然保持当前的一级节能开关状态。
- 「#」修复: 因灯光渐暗，导致即使无线使用时手动关闭节能，灯光未能保持长亮。

##### 2023-02-23 (DN2N)
- 「^」提升一点点按键触发的速度，同时优化新的算法减少某些状态差的轴按键双击出现的可能。

##### 2023-01-23 (DN1N)
- 「^」适用于本键盘按键方案的 更快的首按键响应速度。
- 「^」主控与蓝牙模块之间的通讯，增加两重保险，提升可靠性。
- 「^」1: 每次主控传输命令到蓝牙前，检查之前的命令是否已经完成。
- 「^」2: 按键抬起时，会在发送后确认命令是否成功。如未成功会在下次循环再发，直至确认发送成功。

这次的蓝牙更新后，键盘这端应该不会出现按键后未弹起的情况了。

如果还遇到卡键按键未弹起现象，有可能是蓝牙命令由键盘发送后到电脑接收，这个过程中出了问题。

##### 2023-01-18 (DN1I)

-   「+」增加 优先层 功能。使用瞬时开启的层，临时也被设为优先层，如果此层上有设置按键，则优先响应它，其次才根据所有的层状态从高往低查找。
-   「^」层的逻辑有些变化，把瞬间切换层和其他切换层分开来。现在逻辑上操作更直觉。

它不会破坏以往逻辑，但配合新逻辑，符合更多人对于层切换的期望。具体参看文档里关于层逻辑的新说明。

##### 2023-01-12 (DN1C) 
- 「+」键盘进入节能和从节能唤醒时，增加RGB灯的淡入淡出效果。
- 「+」解开一点封印，增加一点轴灯亮度。
- 「+」引入可调的防抖时间。目前只是预设了两种，NKRO按下防抖时间1ms，6KRO暂时预设是5ms。后续再加入可自定义设置。注意每次键盘重启后默认是NKRO模式，就又会回到1ms。万一部分轴体连击的可尝试临时切换到6KRO看是否有改善。
- 「+」 在可打字的地方按 <kbd>LShift+RShift+N</kbd>时，会打出数字0或6，0代表当前切换到了NKRO全键无冲模式，6代表切换到了6KRO任意6键无冲模式。

##### 2023-01-01 (DN11) 
- 「^」从这个固件开始，USB模式下默认开启NKRO全键无冲，蓝牙模式下依然是6KRO。现在应该很少人使用极老的系统不支持NKRO的了。

##### 2022-06-06 (DM66) 
- 「#」修复：蓝牙模式下，使用文字输出电量无法正常工作。原因是RAM不足。
- 「+」配合本固件，增加一个电阻在蓝牙模块旁边(稍微飞线连接)，可实现不用短接硬件重置蓝牙。

##### 2022-05-29 (DM5T) 
- 「+」二合一按键功能，增加 LT (P)。具体说明见: [按键 | 瞬时开启层](/edit-keymap/layer-tap-key.md)

##### 2022-05-09 (DM59) 
- 「^」改进，休眠唤醒后，默认连接可能非USB的问题。原因是有的主板或系统启动后识别USB需要更长时间。
- 「+」USB连接时，电脑休眠后，支持用键盘唤醒电脑。

##### 2022-04-20 (DM4K)
-   「^」去除一些调试信息，提高运行效率。以及提高稳定性。

##### 2022-03-21(DM3L) 
- 『+』按键防抖升级为疾速防抖，最快可以在按下按键时0.1ms内触发。自研算法，同时使用了三项自研防抖技术。取消了 <kbd>LShift+RShift+N</kbd> 切换NKRO时输出数字。NKRO和6KRO上使用的都是一个模式的防抖了。
- 『+』修饰键组合键的一点点增强，方便实现类似<kbd>Ctrl+H J K L</kbd>或<kbd>Ctrl+N B P F</kbd>为方向键的操作，具体见说明 [修饰键组合键](edit-keymap/mods-key.md)
- 「^」 节能模式下的watchdog逻辑稍微改进了一下。
- 「+」设置为 Tap二合一按键，如果其中是CapsLock，增加一个100ms的延时，让它在MacOS下可以正常切换大小写。
- 「^」 提高 [Esc 与 \`\~](/features/tricky-esc) 功能在单独按触发 Esc 时的响应速度。
- 「^」 改进Lock Mode按键，增加防抖优化。需要F和J按下稳定且其他按键也无任何抖动时，才能退出Lock Mode。
- 「+」 生成的固件体积减小1KB，占用30KB。这样可以使用其他版本的bootloadhid进行固件升级。

##### 2020-10-27 (DKAR)
  - {^} 清除键盘端的蓝牙配对，由 **LShift+RShift+R** 改为 **LShift+RShift+LCtrl+R**，需要多按一个**LCtrl**，可以防止误操作。同时操作完，蓝牙连接状态指示灯会开始指示，可以以此来判定是正确按了此组合键。
  - [+] Shift+Esc输出\~的功能，更加的完善，具体看 [Esc 与 \`\~](/features/tricky-esc)
  - [#] 修复：修饰键 & 瞬时切换层 没有在按下时立即触发的问题。
  - [^] LEDMAP和按键扫描部分做了比较多的精简，提高一些效率（功能无变化）。

##### 2020-07-13 (DK7D)
  - {^} 按键防抖升级为混合防抖，改进某些国产轴有部分连击问题。同时，减少了防抖时间，提高了按键响应速度。
  - {^} 左右Shift+N切换全键无冲时，在可打字的地方会输出0或6，0代表全键无冲，6代表6键无冲。在全键无冲模式下，防抖更激进，响应更快速，但是某些国产轴部分连击问题，可能存在。
  - [+] 左右Shift+P切换节能时，在可打字的地方会输出1或0，1代表节能开启，0代表节能关闭。

##### 2020-05-24 (DK5O)
  - [+] **LShift+RShift+V** 这组命令键，在按的时候，后面会多输出一个-0或-1，代表键盘蓝牙连接状态。
  - {#} 因为有部分人误关掉蓝牙功能，本次更新调整开关蓝牙功能的切换方式，具体见[[ble-series:connection-status|蓝牙开关和连接状态]]
  - {^} 再优化键盘模拟鼠标功能的滚轮部分，之前滚轮速度起飞了。同时USB下移动流畅度再提升一点，速度减一点。

##### 2020-03-07 (DK37)
  - {^} 大幅度提升键盘模拟鼠标功能的流畅和精准性。
  - [^] 大幅减少Send Keymap总共所花的时间。

##### 2020-02-27 (DK2R)
  - [^] 多个可调亮度的RGB模式下，最低亮度由0改为5。
  - [^] 改进Win_Lock功能。之前只是禁用单独的设置的win键（即LWin或RWin），现在可以让所有与win相关的（包括组合键，二合一键等），都不触发win键本身。这样防止误按的效果更佳。
  - [#] 修复：在使用软件重置或者清除修饰时，最新版win10里会触发启动商店版Office(它的默认快捷键是LCtrl+LShift+LAlt+LWin)问题。

##### 2019-11-14 (DJBE)
  - {#}修复问题：因为识别BLE40和BLUP版本错误导致碳纤维夹心版的BLE40使用不正常。

##### 2019-10-14 (DJAE)
  - [+]增加发送KEYMAP到ydkb.io。具体见 [读取按键](/edit-keymap/load-keymap)

##### 2019-10-03 (DJA3)
  - [+]增加蓝牙多设备切换。具体见 [多设备切换](/ble-series/device-switching)

##### 2019-09-18 (DJ9I)
  - [^]提升灯效使用单点亮或涟漪时的续航时间。

##### 2019-09-17 (DJ9H)
  - [#]修复问题：重置蓝牙后初始化时，偶尔重命名未成功。
  - {^}大幅度提升关闭RGB背光时的续航时间。
  - [+]电池服务如果不正常时，电量指示输出44或45。这个是用来辅助判断问题的。

##### 2019-09-12
  - [#]修复问题：使用完全关闭蓝牙功能后，Mac下插USB无法使用（Win下正常）。

##### 2019-09-09
  - {#}修复问题： 左右Shift+R/I/O这三个功能，使用时可能导致蓝牙重新配置或出错。
  - [+]插USB线识别的设备名，后面增加固件日期。比如今天的固件更新后，USB下识别的设备名后面会多一个DJ99,J99分别代表年月日。

##### 2019-08-25
  - [^] 使用 [蓝牙开关和连接状态](/ble-series/connection-status) 完全关闭蓝牙后，键盘的USB可以唤醒电脑了。
  - [^] 有线模式下，默认由NKRO改为6KRO。默认6KRO对各种系统和硬件的兼容更好一些。

##### 2019-08-23
  - {^} 从这个固件开始，BLE40和BLUP的固件合并成一个。
  - [+] 增加蓝牙开关功能，可以完全关闭蓝牙。具体参看：[蓝牙开关和连接状态](/ble-series/connection-status)
  - [+] 增加一个指示灯（A键左边那颗 的轴灯），功能可在LEDMAP里面定义。当它指示时运行灯效时会忽略它，非指示时则它的状态同灯效。
  - [+] 单点亮、涟漪等多个灯效增加底灯的配合灯效。
  - {^} 之前版本的固件直接读取KEYMAP后，蓝牙功能相关的增强按键有的可能需要重新选择设置。
  - {^} 如果要使用YDKB Control来控制灯和修改蓝牙名称等操作，需要重新下载新版(≥190820)。
  - {#} 修复问题：BLUP的连接状态指示工作不正常，并且指示时会引起底灯不亮。
  - [^] 蓝牙连接状态以及低电量的指示灯，由之前的Esc和Q，调整到 A键左边那颗 的轴灯。指示状态时其他灯效保持运行，不再关闭。

##### 2019-08-01
  - [^] 从二级节能(比如超过2.5小时未使用，超过90s无连接，以及Lock Mode)唤醒时也提示蓝牙连接状态。并且，减少每次提示的闪烁时间

