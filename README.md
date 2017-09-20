![Logo](https://raw.githubusercontent.com/uestccokey/EZFilter/master/logo.png)
# EZFilter
一个轻量级，易扩展的Android滤镜框架，支持拍照，视频，图片添加滤镜，支持离屏渲染

### Demo

[下载地址](https://raw.githubusercontent.com/uestccokey/EZFilter/master/demo.apk)

### 功能介绍

1.Camera添加滤镜

2.Camera2添加滤镜（Api21以上）

3.视频添加滤镜（支持自定义播放器）

4.图片添加滤镜（支持离屏渲染）

### 依赖配置

``` gradle
dependencies {
    compile 'cn.ezandroid:EZFilter:1.3.1' // Gradle 3.0以下
    // 或
    implementation 'cn.ezandroid:EZFilter:1.3.1' // Gradle3.0及以上
}
```

### 使用方式

图片加滤镜显示

``` java
new EZFilter.BitmapBuilder()
                .setBitmap(bitmap)
                .addFilter(filter)
                .into(view);
```
图片加滤镜离屏渲染

``` java
Bitmap bitmap = new EZFilter.BitmapBuilder()
                        .setBitmap(bitmap)
                        .addFilter(filter)
                        .capture();

```

视频加滤镜显示

``` java
mPipeline = new EZFilter.VideoBuilder()
                .setVideo(video)
                .setVideoLoop(true)
                .addFilter(filter)
                .into(view);
```

拍照加滤镜（Camera）

``` java
mPipeline = new EZFilter.CameraBuilder()
                .setCamera(camera)
                .addFilter(filter)
                .into(view);
```

拍照加滤镜（Camera2）

``` java
mPipeline = new EZFilter.Camera2Builder()
                .setCamera2(camera2)
                .addFilter(filter)
                .into(view);
```

视频或拍照加滤镜后截图

``` java
mPipeline(new BitmapOutput.BitmapOutputCallback() {
        @Override
        public void bitmapOutput(Bitmap bitmap){
        }
    },true); // 第二个boolean参数表示是否截原图还是截添加了滤镜之后的图
```
