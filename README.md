# ROG Strix G16 G614JVR    Hackintool Mac OS Tahoe   N-key 无限枚举/复位/失灵

Mac OS Tahoe
0.先打好USB端口补丁，我的键盘是走内置USB接口的HID复合式键盘。
1.mac终端运行此代码‘ioreg -l -w0 | grep -B 5 -A 20 "bInterfaceNumber"’
2.把结果发给deepseek或者其他的Ai
3.让Ai判断哪一些键盘的内置接口延迟过高，然后做针对性的kext屏蔽补丁。
4.kext驱动只能放在opencore kext 列表的最末端，避免发生未知bug。
5.就比如我是1和3延迟过高，导致发生的无限枚举/复位。导致上电又断又上电。
  注：常见的现象是打字时好时坏，长文本无法长按退格键删除（长按指令由于无限枚举而中断导致）
info：……\NKeyBlocker.kext\Contents\Info.plist
  注：此ktxt补丁不稳定，就尤其是有时候会卡码无法进入系统，但进入系统之后能极大改善键盘失灵问题




# ROG Strix G16 G614JVR, Hackintool, N-key infinite enumeration / reset / malfunction

Mac OS Tahoe
1. Apply USB port patches first. My built-in keyboard is a composite HID keyboard connected via an internal USB port.
2. Run this command in macOS Terminal: `ioreg -l -w0 | grep -B 5 -A 20 "bInterfaceNumber"`
3. Send the output to DeepSeek or another AI.
4. Ask the AI to identify which internal keyboard interfaces have excessive latency, then create targeted kext blocking patches.
5. Kext drivers must be placed at the **end** of the OpenCore kext list to prevent unexpected bugs.
6. For example, interfaces 1 and 3 had high latency on my machine, which triggered infinite enumeration/reset, causing the device to continuously power-cycle and disconnect.

Note: Common symptoms include intermittent keyboard input failure, and inability to hold backspace for bulk text deletion. The hold command gets interrupted by repeated enumeration cycles.
info：……\NKeyBlocker.kext\Contents\Info.plist
Note: This kext patch is unstable. It may sometimes stall during boot and prevent the system from loading. However, once the system successfully boots, it greatly mitigates keyboard failure issues.

