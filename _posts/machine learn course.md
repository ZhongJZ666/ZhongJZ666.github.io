---
layout: post
title: 机器学习笔记
date: 2024-03-20
categories: [机器学习]
toc: true
---

■ 整数编码(sklearn.preprocessing.LabelEncoder）：每个唯一的字符串值被转换为一个唯一的整数。
`LabelEncoder`是scikit-learn库中的一个工具，用于将分类标签转换为整数值。它通常用于将目标变量（y值）从字符串转换为数值，以便机器学习算法能够处理。
使用方法

```python
from sklearn.preprocessing import LabelEncoder
# 假设'颜色'和'尺寸'是需要编码的分类特征
categorical_features = ['颜色', '尺寸']

# 使用LabelEncoder对每个分类特征进行编码
encoders = {}
for feature in categorical_features:
    encoder = LabelEncoder()
    data[feature] = encoder.fit_transform(data[feature])
    encoders[feature] = encoder
```
其中feature是需要处理的特征，data为导入的数据集名称


pandas库中整数编码使用pandas.factorize()方法
■ 独热编码(sklearn.preprocessing.OneHotEncoder)：每个唯一的字符串值对应一个列。如果某行的特定列值为该唯一值，则该列的值为1，否则为0。
pandas库中独热编码使用get_dummies方法

或者使用pandas库中方法将类型进行转换，将object类型的文件转化为分类类型

```python
for col in data.columns:

            if data[col].dtype == 'object':

                data[col] = data[col].astype('category').cat.codes
```

整数编码（Ordinal Encoding）和独热编码（One-Hot Encoding）的区别：

整数编码（Ordinal Encoding）：

定义：将分类特征映射为有序整数值（例如，颜色：红=1，绿=2，蓝=3）。

假设：假设分类值之间存在顺序或等级关系。

适用模型：树基模型（决策树、随机森林、梯度提升）可以处理整数编码，因为它们可以捕捉到值之间的顺序关系。

注意：不适合线性模型，因为线性模型会将整数值视为数值特征，可能导致错误的解释。

独热编码（One-Hot Encoding）：

定义：将分类特征转换为二元向量（例如，颜色：红=[1,0,0]，绿=[0,1,0]，蓝=[0,0,1]）。

假设：不假设分类值之间存在顺序关系。

适用模型：适合大多数机器学习模型，包括线性模型和树基模型。独热编码是线性模型的首选，因为它避免了数值假设。

注意：可能导致维度灾难（增加特征维度），但在树基模型中通常不是问题。

实验一中的线性模型：

使用独热编码，以避免由于整数编码的数值假设而导致的潜在问题。