# 构建一个交通标志识别分类器

## Step0:载入数据

## Step1:数据集摘要和探索
1.观察了数据集的情况和特征，训练集一共34799个，验证集一共4410个，测试集一共12360个，交通标示种类43个。  
2.列举了每一类交通标示的数目。  
3.通过不同样式的表格对数据集有了深入的了解。  

## Step2:设计并训练一个模型结构

### 模型一
convolution 1: 32x32x1  -> 28x28x12 -> relu -> 14x14x12 (pooling)  
convolution 2: 14x14x12 -> 10x10x25 -> relu -> 5x5x25   (pooling)  
flatten: 5x5x25   -> 625  
drop out: 625      -> 625  
linear: 625      -> 300  
linear: 300      -> 100  
linear: 100      -> 43  
训练10次后，得到交通标志识别分类器的一个模型。在训练集上的准确率为0.998；在验证集上的准确率为0.929；在测试集上的准确率为0.933。

### 模型二
对模型一进行了一些参数上的调整  
convolution 1: 32x32x1  -> 28x28x12 -> relu -> 14x14x12 (pooling)  
convolution 2: 14x14x12 -> 10x10x25 -> relu -> 5x5x25   (pooling)  
flatten: 5x5x25   -> 625  
drop out: 625      -> 625  
linear: 625      -> 400  
linear: 400      -> 200  
linear: 200      -> 43  
训练10次后，得到交通标志识别分类器的另一个模型。在训练集上的准确率为0.999；在验证集上的准确率为0.945；在测试集上的准确率为0.943。与模型一比较有了准确率有了一定的提升，效果更优。