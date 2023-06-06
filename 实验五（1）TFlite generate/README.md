# TFlite generate
运行下面代码：

```python
import os

import numpy as np

import tensorflow as tf
assert tf.__version__.startswith('2')

from tflite_model_maker import model_spec
from tflite_model_maker import image_classifier
from tflite_model_maker.config import ExportFormat
from tflite_model_maker.config import QuantizationConfig
from tflite_model_maker.image_classifier import DataLoader

import matplotlib.pyplot as plt
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/fdddb689387d4e16bef39ec6bd5dd0e2.png#pic_center)



发现报错如上：问题是numpy版本过新，修改一下版本

```
pip install numpy==1.23.5
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/4c265d3a08fb40c589614eb6ad938ff9.png#pic_center)


在运行导包代码：

发现缺少该文件

![在这里插入图片描述](https://img-blog.csdnimg.cn/352d2a84404e4655a3e6d549a308c4b5.png#pic_center)


在终端输入以下内容：

```py
sudo apt-get -y install libusb-1.0-0-dev
```



如果发生以下报错：

![在这里插入图片描述](https://img-blog.csdnimg.cn/03c482f64ad34385879cfba6000806af.png#pic_center)


更新一下apt：

```
sudo apt-get update
```

在执行：

```
sudo apt-get -y install libusb-1.0-0-dev
```

之后在重新运行

```python
import os

import numpy as np

import tensorflow as tf
assert tf.__version__.startswith('2')

from tflite_model_maker import model_spec
from tflite_model_maker import image_classifier
from tflite_model_maker.config import ExportFormat
from tflite_model_maker.config import QuantizationConfig
from tflite_model_maker.image_classifier import DataLoader

import matplotlib.pyplot as plt
```

导包成功！

![在这里插入图片描述](https://img-blog.csdnimg.cn/118b71ae30634aab8c451c9c40b7ad59.png#pic_center)


## 获取数据集：

```python
image_path = tf.keras.utils.get_file(
      'flower_photos.tgz',
      'https://storage.googleapis.com/download.tensorflow.org/example_images/flower_photos.tgz',
      extract=True)
image_path = os.path.join(os.path.dirname(image_path), 'flower_photos')

```

这里从`storage.googleapis.com`中下载了本实验所需要的数据集。`image_path`可以定制，默认是在用户目录的`.keras\datasets`中。

![在这里插入图片描述](https://img-blog.csdnimg.cn/4259aa5991a54d629d8c3b02769c83dd.png#pic_center)


## 运行示例

一共需4步完成。
第一步：加载数据集，并将数据集分为训练数据和测试数据。

```
data = DataLoader.from_folder(image_path)
train_data, test_data = data.split(0.9)

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f8151da44a9749a7b3efc7fc6cc83c26.png#pic_center)


第二步：训练Tensorflow模型

```
model = image_classifier.create(train_data)

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f1c3deb061c74b8f8b074ab5d83287d1.png#pic_center)


第三步：评估模型

```
loss, accuracy = model.evaluate(test_data)
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/10272605472844e8bcc6a6cc39963174.png#pic_center)


第四步，导出Tensorflow Lite模型

```
model.export(export_dir='.')
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/0c183937dba042aeb4339568a79244c9.png#pic_center)



这里导出的Tensorflow Lite模型包含了元数据(metadata),其能够提供标准的模型描述。导出的模型存放在Jupyter Notebook当前的工作目录中。



