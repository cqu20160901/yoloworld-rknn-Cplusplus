# yoloworld_rknn_Cplusplus

yoloworld 瑞芯微 rknn 板端 C++部署，使用平台 rk3588。模型转换参考 [【yolov9 瑞芯微芯片rknn部署、地平线芯片Horizon部署、TensorRT部署】](https://blog.csdn.net/zhangqian_1/article/details/136321979)  。

模型文件比较大存放路径[【rknn模型链接】](https://github.com/cqu20160901/yolov9_rknn_Cplusplus/releases/tag/v1.0.0)

## 编译和运行

1）编译

```
cd examples/rknn_yoloworld_demo_open

bash build-linux_RK3588.sh

```

2）运行

```
cd install/rknn_yoloworld_demo_open

./rknn_yoloworld_demo

```

注意：修改模型、测试图像、保存图像的路径，修改文件为src下的main.cc

```

int main(int argc, char **argv)
{
    char model_path[256] = "/home/zhangqian/rknn/rknpu2_1.4.0/examples/rknn_yoloworld_demo_dfl_open/model/RK3588/yolo_world_v2.rknn";
    char image_path[256] = "/home/zhangqian/rknn/rknpu2_1.4.0/examples/rknn_yoloworld_demo_dfl_open/test.jpg";
    char save_image_path[256] = "/home/zhangqian/rknn/rknpu2_1.4.0/examples/rknn_yoloworld_demo_dfl_open/test_result.jpg";

    detect(model_path, image_path, save_image_path);
    return 0;
}
```


# 测试效果

onnx 测试结果
![test_onnx_result](https://github.com/cqu20160901/yoloworld-rknn-Cplusplus/assets/22290931/fe7d1d1e-ff16-4d98-bd71-28c1c56f3648)


板端测试结果
冒号“:”前的数子是coco的80类对应的类别，后面的浮点数是目标得分。（类别:得分）
![image](https://github.com/cqu20160901/yoloworld-rknn-Cplusplus/blob/main/examples/rknn_2.0_yoloworld_demo/test_result.jpg)



把板端模型推理和后处理时耗也附上供参考，使用的芯片rk3588，模型输入640x640，检测类别80类。


![image](https://github.com/cqu20160901/yoloworld-rknn-Cplusplus/assets/22290931/cb36f43f-88e2-41ee-8a7b-c4718d52fb43)

