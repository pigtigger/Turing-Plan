# 基于Pytorch训练YOLO v4-Tiny目标检测模型

## 文件准备

YOLO v4-Tiny模型可从GitHub上获得。首先在任意位置新建一个自己的项目文件夹用于存放代码文件（注意文件夹名字及路径中不能有**中文和空格**，否则之后会出现各种问题），打开命令行cd到此文件夹下，运行
```
git clone https://github.com/pigtigger/Tuling-Plan.git
```
也可以直接从GitHub页面上下载压缩包，或是从百度网盘上下载，
链接: [https://pan.baidu.com/s/1sOv2ToKaZpwr5vbQv0OzIQ](https://pan.baidu.com/s/1sOv2ToKaZpwr5vbQv0OzIQ) 提取码: x9ag

下载得到的YOLO v4-Tiny文件夹架构如下
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601520880119-092bfb35-17e5-4399-a20b-8d12f15fb7b9.png#align=left&display=inline&height=333&margin=%5Bobject%20Object%5D&name=image.png&originHeight=665&originWidth=212&size=21684&status=done&style=none&width=106)

为了简化模型的训练过程，通常我们都会利用已预训练过的模型权重进行迁移学习，也就是将预训练好的模型权重参数作为自己模型的初始权重参数进行训练。因此，除了代码，还需要下载预训练好的模型权重文件。

可以从百度网盘上下载权重文件，有两个文件可供选择，分别是利用voc数据集预训练的yolov4_tiny_voc.pth和利用coco数据集预训练的yolov4_tiny_weights_coco.pth，下载好后需要将权重文件放入model_data文件夹下。
链接: [https://pan.baidu.com/s/1eze6GTthd8x0kaP0Dysb6g](https://pan.baidu.com/s/1eze6GTthd8x0kaP0Dysb6g) 提取码: 01pr

## 预训练模型测试

1、Python运行predict.py示例程序，输入img/street.jpg，可以看到打开了img文件夹下名为street.jpg的图片，图中各种物体已经被框出并分类。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601539858926-b9911878-3fd9-4e7d-b6cd-8f5e688753cb.png#align=left&display=inline&height=427&margin=%5Bobject%20Object%5D&name=image.png&originHeight=854&originWidth=857&size=1624476&status=done&style=none&width=428.5)
如出现FileNotFoundError错误，请学习python工作目录、相对路径等知识，有能力的同学可使用os.path模块改进代码，一劳永逸地解决相关问题。

2、Python运行video.py示例程序可以打开摄像头进行检测。

## 模型训练
### 一、数据准备
训练模型需要大量数据，有能力的同学可以自行在网上寻找高质量的数据集使用，这里我提供一些戴口罩与未带口罩的人脸图片，供同学们下载选用。
链接：[https://pan.baidu.com/s/1pMQEiehMCj2y7dgYpUfQ3A](https://pan.baidu.com/s/1pMQEiehMCj2y7dgYpUfQ3A) 提取码: u5x9

图片下载下来并挑选后，需要放到/VOCdevkit/VOC2007/JPEGImages文件夹下。注意，这些图片的文件名是混乱的，为了方便后续的标注和训练，应当将它们的文件名变成规律的，如“0000.jpg”、“0001.jpg”等。实现方法请同学们自行探索。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601543242403-9af2ec75-e572-4364-b86c-b54ac74294ea.png#align=left&display=inline&height=372&margin=%5Bobject%20Object%5D&name=image.png&originHeight=744&originWidth=1404&size=1140597&status=done&style=none&width=702)
此外，有能力的同学可以利用数据增强（Data Augmentation）来扩充数据集，提高模型的鲁棒性。

### 二、数据标注
接下来进行数据标注，需要使用标注软件，这里用的是labelImg工具，可以从[此处](https://github.com/tzutalin/labelImg)下载并学习安装方法。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601565395256-cf9dd3f9-3611-4ac2-adbe-d95334f0934d.png#align=left&display=inline&height=411&margin=%5Bobject%20Object%5D&name=image.png&originHeight=821&originWidth=988&size=64877&status=done&style=none&width=494)
运行labelImg，打开界面
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601544661980-a32e7bfe-6a53-43c5-8f48-6398d856736c.png#align=left&display=inline&height=485&margin=%5Bobject%20Object%5D&name=image.png&originHeight=970&originWidth=1451&size=73750&status=done&style=none&width=725.5)
点击界面左上的Open Dir选择图片文件夹，即/VOCdevkit/VOC2007/JPEGImages，之后点击Change Save Dir选择标签存储文件夹为/VOCdevkit/VOC2007/Annotations，标注格式选择PascalVOC。

点击Create RectBox就可以进行框选标注，框选带口罩或不戴口罩的人脸，在弹出的标签窗口中输入mask或un_mask即可进行标注，之后点Save保存，Annotations文件夹下就生成了xml格式的标签文件，之后点击Next Image继续进行标注（活用快捷键W、A、D、Ctrl+S）。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601545720282-1e476f53-962c-4afa-80f6-c6074509846f.png#align=left&display=inline&height=470&margin=%5Bobject%20Object%5D&name=image.png&originHeight=940&originWidth=1223&size=990084&status=done&style=none&width=611.5)
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601545580909-7e617d33-c499-4fa5-a9c0-252aa57b012d.png#align=left&display=inline&height=471&margin=%5Bobject%20Object%5D&name=image.png&originHeight=941&originWidth=1224&size=964487&status=done&style=none&width=612)
标注完成后，Annotations文件夹下会生成大量的xml文件
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601561077697-46c7039c-7edd-4adb-86c6-641cf5bc68bf.png#align=left&display=inline&height=422&margin=%5Bobject%20Object%5D&name=image.png&originHeight=844&originWidth=1034&size=142498&status=done&style=none&width=517)
打开任意xml文件，格式如下
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601561152543-812b9a28-da1c-44ca-aa2b-21b63c52cde8.png#align=left&display=inline&height=412&margin=%5Bobject%20Object%5D&name=image.png&originHeight=823&originWidth=1422&size=71660&status=done&style=none&width=711)
但此时标注文件尚不能被YOLO模型读取，要运行/VOCdevkit/VOC2007文件夹下的voc2yolo4.py提取文件索引，之后运行根目录下的voc_annotation.py，运行前需要将classes改成自己需要的classes，即mask和un_mask。运行后索引和标注信息被写入到了根目录下的2007_train.txt文件中。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601562030711-02b48a5f-9938-4041-a45c-df184a5ef5d0.png#align=left&display=inline&height=411&margin=%5Bobject%20Object%5D&name=image.png&originHeight=821&originWidth=1419&size=207556&status=done&style=none&width=709.5)

### 三、训练模型
接下来进入模型训练的环节，首先要在model_data下新建一个txt文档，文档中输入需要分的类，同时在train.py中将classes_path指向该文件。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601562592228-3913a95a-fd53-452f-ac8e-43bb962cc0c0.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=187&originWidth=1416&size=12689&status=done&style=none&width=708)
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601562709534-846f9b6c-45b6-4cd9-ba12-d459fad9a5d5.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=187&originWidth=597&size=18143&status=done&style=none&width=298.5)
之后，在train.py中设置超参数，如学习率lr、批量大小Batch_size、训练世代数等，可以先使用默认的值进行实验，之后再根据情况进行修改。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601563389173-cd57b11f-dc2d-4299-b87b-b49f073457ff.png#align=left&display=inline&height=170&margin=%5Bobject%20Object%5D&name=image.png&originHeight=339&originWidth=820&size=34321&status=done&style=none&width=410)
注意，代码中利用torch.save模块将训练出的模型权重文件保存在根目录的logs文件夹下，保存频率为每世代保存一次，同学们可以根据自己的意愿修改保存频率及路径。

一切就绪后，运行train.py开始训练，注意观察loss的下降。训练结束后logs文件夹下得到诸多权重文件。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601564404771-c930c7da-b3ce-4c44-bc8f-1c3b9df68bd7.png#align=left&display=inline&height=363&margin=%5Bobject%20Object%5D&name=image.png&originHeight=726&originWidth=1403&size=138252&status=done&style=none&width=701.5)
找到最后世代的权重文件，将根目录下yolo.py中的model_path指向该权重文件，并将classes_path指向之前在model_data下创建的txt文件。
![image.png](https://cdn.nlark.com/yuque/0/2020/png/821701/1601565023802-1d839645-ed7d-4b6f-aaae-b5ff5cac1912.png#align=left&display=inline&height=173&margin=%5Bobject%20Object%5D&name=image.png&originHeight=345&originWidth=905&size=35950&status=done&style=none&width=452.5)
接下来同测试预训练模型时一样，运行predict.py和video.py进行模型效果的测试。如测试结果不够理想，可以尝试修改超参数、扩大数据集等方法。
