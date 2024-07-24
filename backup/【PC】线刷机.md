首先，手机连接USB数据线到电脑，准备好ROM,包；
1.手机进入BootLoader模式，也就是这个页面：
![1821978-20191212152855411-1213984289](https://github.com/user-attachments/assets/d553d9d1-9dee-44d9-bc4d-b8ecc31ff146)
2.点击高级--ADB Sideload
![1821978-20191212152855650-326535847](https://github.com/user-attachments/assets/92397cfd-cc33-478d-93e9-eb8c812ac3a0)
3.滑动开始
![1821978-20191212152856164-2044241004](https://github.com/user-attachments/assets/d45a5a46-0123-4f6f-8141-4d19890d7822)
4.执行命令  ` adb sideload G:\fastboot\e-0.7-o-2019111430687-dev-polaris.zip`
 也就是  `adb sideload XX/XX.ZIP`    adb sideload后面的XX/XX.ZIP为ROM文件存放路径。
5.完成，重启手机！