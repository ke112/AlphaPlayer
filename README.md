# alpha_player_plugin
对字节跳动官方原生组件AlphaPlayer一个flutter plugin封装

具体实现功能见字节跳动官方github:
https://github.com/bytedance/AlphaPlayer

### 关于透明视频
* 透明视频的播放，对于webm格式的视频，在h5上面是很容易播放的
* 但是对于android或者flutter来说，尤其flutter的官方video_player是不支持带有透明通道的视频播放的
* 但是对于字节跳动这个方案，综合起来还是比较合适的
* 比如我们想播一个炫酷的礼物特效，要求有透明效果，这种用AlphaPlayer实现最好不过了
* 可以这个插件目前没有flutter版本的，那么就来手撸一个

### 运行效果

<img src="./demo_show.gif" width=320 />

### 特点
* 支持android和ios双端
* 支持播放手机本地mp4文件
* 简单易用，直接传入path地址

### 快速接入

#### 添加依赖
`alpha_player_plugin: ^0.0.1`

#### 用法
##### AlphaPlayerView
```
AlphaPlayerController controller = AlphaPlayerController();

AlphaPlayerView(
  controller: controller,
  width: xxx,
  height: xxx,
)

controller.start(videoPath);
```
##### AlphaPlayerSimpleView(对AlphaPlayerView的简单封装)

```
AlphaPlayerSimpleView(
  path: videoPath,
  width: xxx,
  height: xxx,
)

AlphaPlayerSimpleView(
  path: videoPath,
  width: xxx,
  height: xxx,
  isLooping: false,
  onStarted: (ct) {
    // 可以拿到controller,进行其他操作
    controller = ct;
  },
  onCompleted: (videoPath) {
    // isLooping为false 才能拿到播放结束的回调
  },
)
```
##### AlphaPlayerSimpleView说明
| 属性        | 描述                                       |
| ----------- | ------------------------------------------ |
| path        | 视频文件路径                               |
| width       | 宽度                                       |
| height      | 高度                                       |
| align       | 视频裁剪对齐方式，详见AlphaPlayerScaleType |
| isLooping   | 是否循环播放                               |
| onStarted   | 视频开始播放，可拿到controller             |
| onCompleted | 视频播放结束（仅在isLooping为false时生效） |

### 小提示
项目目录下test_video文件夹下提供了测试视频，可以传到手机上运行example进行测试


视频横向分辨率最好不要超过1920，真实视频的960，因为部分低端android手机不支持太高分辨率的播放
https://github.com/google/ExoPlayer/issues/4966


### 其他
如果对你有帮助，动动小手给一个star，谢谢。

目前该库支持的就是上述这些功能，如果有其他需求问题或者bug，欢迎提issue，会尽力帮助大家解决
