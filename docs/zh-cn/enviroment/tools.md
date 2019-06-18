# 录屏工具

Camtasia studio 2018是继9之后最新推出的一款屏幕录像视频编辑软件，从该版本之后TechSmith公司也学大多数软件一样使用年份来命名，该软件拥有强大的屏幕录像、视频的剪辑和编辑、视频菜单制作、视频剧场和视频播放功能等功能，能在任何颜色模式下轻松地记录屏幕动作，包括影像、音效、鼠标移动的轨迹，解说声音等等。

## 安装破解

1. 下载安装包。

   **TechSmith Camtasia官网：**<https://www.techsmith.com/video-editor.html>

   **Camtasia中文网**：[http://camtasiacn.com](http://camtasiacn.com/)

2. 双击运行安装包，安装Camtasia studio 2018。

3. **断开网络**，开始破解。

4. 打开文件夹`C:\ProgramData\TechSmith\Camtasia Studio 18`。

   > [!Tip]
   >
   > `\ProgramData`是隐藏文件夹。

5. 打开`RegInfo.ini`文件，可以看到只有如下的内容：

   ```bash
   [RegistrationInfo]
   ValidationData3=1
   
   RegistrationKey=
   
   RegisteredTo=
   
   ValidationData1=
   
   ValidationData2=
   ```

   

6. 复制以下内容覆盖`RegInfo.ini`中的相同参数，保存退出。

   ```bash
   [RegistrationInfo]
   ValidationData3=1
   
   RegistrationKey=CYNTE-LZ29A-CKLCC-CAS5Y-DRFAD
   
   RegisteredTo=shawn
   
   ValidationData1=3
   
   ValidationData2=1
   ```

   

7. 右击`RegInfo.ini`，将其文件属性设置为`只读`。

8. 启动Camtasia studio 2018，查看“帮助 > 关于Camtasia”。

   显示“多用户许可”，注册破解成功。

## 使用说明

### 录屏

1. 选择“文件 > 新建录制”，或使用快捷键“CTRL+R”，调出“录制”工具。

2. 选择录制区域：全屏或自定义（可以手动选择录制区域）。

3. 配置录制输入：摄像头和音频。

4. 单击“rec”，系统提示“开始录制”。

   按“F10”可停止录制。

### 编辑

录屏完毕后，可进行编辑，比如：添加注释、转场效果、行为和动画（缩放）等等。

![](../../img/test.gif)

### 生成

可自定义生成mp4、wmv、avi、gif等文件。以生成git图为例：

1. 选择“分享 > 自定义生成 > 新建自定义生成”，系统显示“生成向导”。

2. 选择“GIF - 动画文件”，单击“下一步”。

3. 后续根据需要进行配置，或直接使用默认配置，单击“下一步”。

4. 配置输出文件名，单击“完成”。

   可在目标文件夹下找到对应的git文件。