# macOS的配对

**特别注意：** MacOS 10.13.6，有好几个人反馈回使用BLE HID的设备有问题，不仅限于键盘，具体情况就是能配对能连接，但是无法输入。这种情况暂时的解决方法只有升级到10.14。

macOS对蓝牙4.0\(BLE4.0\)的第三方HID设备，兼容不是特别友好。所以出现配对不了搜索不了键盘的情况，按下面进行操作。

首先是正常情况下，很简单，只要不是特别老的mac电脑，硬件都应该支持蓝牙4.0。

  - 要用一个设备连接到键盘，首先务必保证键盘处于未连接状态，这样才可以被搜索到。
  - 从蓝牙管理里面搜索到键盘，点击连接。在搜索键盘的时候，一开始显示出来的，不一定是键盘名称，可能是一个地址，一样直接点击连接就好。

<div style="width: 600px">

![](/assets/mac-pairing-001.png)
![](/assets/mac-pairing-002.png)
</div>

## 如果出现无法搜索到的情况：

Mac及iOS对蓝牙服务的要求更严格。

如果这个键盘有更新的最新固件是2019.6.20之后的，那么，重新生成一个固件，然后刷入键盘。之后再 <key>LShift+RShift+r</key> 同时一起按，然后Mac下应该能直接搜索到了。并且成功连接后显示的图标是一个键，而不是后面截图里的蓝牙图标。

如果是DKAD（2020.10.13）之后的固件，使用 <key>LShift+RShift+LCtrl+r</key>。

如果还是不行，再尝试下面补充的方法，使用Adafruit Bluefruit LE Connect进行连接。

## 无法搜索到时的补充：

进入App Store，搜索“Bluefruit LE"，找到下面这个应用，安装。
<div style="width: 600px">

![](/assets/mac_pairing_01.png)
</div>

然后打开这个应用，在这个应用里，可以搜索到键盘了。点击，并连接。之后就可以正常使用了。
<div style="width: 600px">

![](/assets/mac_pairing_02.png)
</div>

在蓝牙偏好里，也能看到键盘是已连接了。用Adafruit的软件连上时，显示的图标可能就是一个蓝牙而不是键盘。所以尽量不使用这种方式。
<div style="width: 600px">

![](/assets/mac_pairing_03.png)
</div>

## 如果遇到其他问题

如果出现<html><font color="blue">配对或连接异常，包括但不限于无法配对，配对后重新开关电源会连接不上,电脑反复显示已连接已配对等</font></html>，可使用键盘的<html><font color="red">清除已配对（左右Shift+R或自行设置）</font></html>功能，这个操作是清除蓝牙模块内的所有已配对信息，必须执行它之后再在设备上重新配对，而不是仅在设备上删除蓝牙键盘再配对，那样不一定能解决问题。
