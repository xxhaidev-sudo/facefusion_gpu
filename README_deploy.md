# 本地化部署方案.
基于官方github地址：https://github.com/facefusion/facefusion 截至日期为：2026-03-31

## cpu环境部署步骤：
1. 推荐使用conda虚拟环境，如果没有anaconda请自行安装。 官网地址：https://www.anaconda.com/products/individual

2. 创建cpu环境
```
conda create -n facefusion python=3.12
```

3. 激活环境并安装依赖包
```
# 激活环境
conda activate facefusion
# 安装依赖包
pip install -r requirements.txt
```

4. 运行程序
```
python facefusion.py run
```

5. 打开浏览器访问：http://127.0.0.1:7860 （默认）/ http://0.0.0.0:7860 (需替换为实际ip地址)-----查看ip地址： windows: ipconfig /all  mac/linux: ifconfig

6. 运行程序后，会自动下载部分模型，请耐心等待， 在前端界面选择某些模型后， 也会触发模型的自动下载， 详情下载信息请关注控制台输出。

7. 结束（祝你好运）


## gpu环境部署步骤：---- 如果没有安装cuda和cudnn请忽略此段, 自行安装请搜索相关教程此处不做讲解。
1. 推荐使用conda虚拟环境，如果没有anaconda请自行安装。 官网地址：https://www.anaconda.com/products/individual

2. 创建gpu环境
```
conda create -n facefusion-gpu python=3.12
```

3. 激活环境并安装依赖包
```
# 激活环境
conda activate facefusion-gpu
# 安装依赖包
pip install -r requirements_cuda.txt
```

4. 运行程序
```
python facefusion.py run
```

5. 打开浏览器访问：http://127.0.0.1:7860 （默认）/ http://0.0.0.0:7860 (需替换为实际ip地址)-----查看ip地址： windows: ipconfig /all  mac/linux: ifconfig

6. 运行程序后，会自动下载部分模型，请耐心等待， 在前端界面选择某些模型后， 也会触发模型的自动下载， 详情下载信息请关注控制台输出。

7. 结束（祝你好运）


#### 其他内容
**默认模型下载位置**：当前项目目录下：.assets/models
**关闭局域网访问**： 运行程序时，添加参数：python facefusion.py run --server-name 127.0.0.1 --server-port 7860
**调整默认启动端口**： facefusion.ini配置文件中， 修改[uis]下 server_port 和 server_name 即可.


**web页面参数介绍**

![alt text](docx\image.png)
- face_swapper: 替换人脸
- face_debugger: 显示的展示标记点

![alt text](docx\image2.png)
- face_swapper_model: 替换人脸模型, 推荐 hyperswap/ inswapper
- face_swapper_pixel_boost: 替换人脸的像素调整 -- 根据实际情况调整
- face_swapper_weight: 替换人脸的权重 -- 根据实际情况调整

![alt text](docx\image3.png)
- execution_providers: 运行环境, cpu环境仅可选择cpu, gpu环境可选择cpu/cuda/tensorrt
- execution_thread_count: 运行线程数, 根据实际情况调整

![alt text](docx\image4.png)
- download_models: 模型下载地址，github/huggingface 推荐全选。

![alt text](docx\image5.png)
- video_memory_strategy: 显存策略, 根据实际情况调整, strict / moderate / tolerant => 严格 / 中等 / 宽松
- system_memory_limit: 显存限制, 根据实际情况调整, 默认为0自动

![alt text](docx\image6.png)
- source：需要提供的人脸图片, 用于进行替换
- target：需要替换的人脸图片/视频.
- output_path：输出路径 --- 不建议调整
- output：完成后的图片/视频展示，推荐直接下载。

![alt text](docx\image7.png)
- ui_workflow: 运行模式，instant_runner / job_runner / job_manager => 即时运行 / 任务运行 / 任务管理
- start: 开始运行
- clear: 清空输出

![alt text](docx\image8.png)
- preview: 预览窗口， 首次调整模型后预览结果会需要重新加载模型做处理， 请耐心等待。
- preview_model: 预览方式，frame by frame / face by face => 逐帧预览 / 逐人脸预览
- preview_pesolution: 预览分辨率，根据实际情况调整

![alt text](docx\image9.png)
- trim frame: 裁剪帧数，根据实际情况调整
- face selector mode: 人脸选择方式，根据实际情况调整， 默认reference, one / many
- reference face: 参考人脸，仅选择 reference 时出现

![alt text](docx\image10.png)
- face_selector_order: 人脸选择顺序，如果有多个人脸替换， 请自行选择合适的顺序
- face_selector_gender: 人脸选择性别，male / female / none
- face_selector_race: 人脸选择种族，white / black / latino / asian / indian / arbaic / none
- face_selector_age: 人脸年龄选择，自行调整
- reference_face_distance: 参考人脸距离，自行调整
- face_occluder_model: 人脸遮挡模型，自行调整
- face_parser_model: 人脸解析模型，自行调整

![alt text](docx\image11.png)
- face_mask_types: 人脸遮罩，打开face_debugger可查看选择的区域，自行调整
- face_mask_blur: 人脸遮罩模糊度，边缘过度清晰度，自行调整
- face_mask_padding_top: 人脸遮罩填充距离，自行调整
- face_mask_pandding_right: 人脸遮罩填充距离，自行调整
- face_mask_padding_bottom: 人脸遮罩填充距离，自行调整
- face_mask_padding_left: 人脸遮罩填充距离，自行调整

![alt text](docx\image12.png)
- face_detector_model: 人脸检测模型，推荐yolo_face, 其余模型匹配程度自行查看
- face_detector_size: 人脸检测分辨率，自行调整

![alt text](docx\image13.png)
- face_detector_margin: 人脸检测边距，自行调整
- face_detector_angles: 人脸检测角度，自行调整
- face_detector_score: 人脸检测分数，自行调整
- face_landmarker_model: 人脸关键点模型，自行调整
- face_landmarker_score: 人脸关键点分数，自行调整

![alt text](docx\image14.png)
- options： keep-temp: 保存临时文件，自行调整， 默认不启用， 启用后不会删除临时文件，否则当前台任务执行玩不并清楚时自动删除临时文件。
