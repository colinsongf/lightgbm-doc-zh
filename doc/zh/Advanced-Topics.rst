进阶主题
===============

缺失值的处理
--------------------

-  LightGBM 通过默认的方式来处理缺失值，你可以通过设置 ``use_missing=false`` 来使其无效。

-  LightGBM 通过默认的的方式用 NA (NaN) 去表示缺失值，你可以通过设置 ``zero_as_missing=true`` 将其变为零。

-  当设置 ``zero_as_missing=false`` （默认）时，在稀疏矩阵里 (和LightSVM) ，没有显示的值视为零。

-  当设置 ``zero_as_missing=true`` 时， NA 和 0 （包括在稀疏矩阵里，没有显示的值）视为缺失。


分类特征的支持
---------------------------

-  当使用本地分类特征，LightGBM 能提供良好的精确度。不像简单的 one-hot 编码，LightGBM 可以找到分类特征的最优分割。
   相对于 one-hot 编码结果，LightGBM 可以提供更加准确的最优分割。

-  用 ``categorical_feature`` 指定分类特征
   参考 `Parameters <./Parameters.rst>`__ 的参数 ``categorical_feature`` 

-  首先需要转换为 int 类型，并且只支持非负数。
   将其转换为连续范围更好。

-  使用 ``min_data_per_group``, ``cat_smooth`` 去处理过拟合（当 ``#data`` 比较小，或者 ``#category`` 比较大）

-  对于具有高基数的分类特征(``#category`` 比较大), 最好把它转化为数字特征。

LambdaRank
----------

-  标签应该是 int 类型，较大的数字代表更高的相关性（例如：0：坏，1：公平，2：好，3：完美）。

-  使用 ``label_gain`` 设置增益（重量）的 ``int`` 标签。

-  使用 ``max_position`` 设置 NDCG 优化位置。

参数优化
-----------------

-  参考 `参数优化 <./Parameters-Tuning.rst>`__ .

并行学习
-----------------

-  参考 `并行学习指南 <./Parallel-Learning-Guide.rst>`__ .

GPU 的支持
-----------

-  参考 `GPU 教程 <./GPU-Tutorial.rst>`__ 和 `GPU Targets <./GPU-Targets.rst>`__

GCC 用户的建议 (MinGW, \*nix)
--------------------------------------------

-  参考 `gcc 建议 <./gcc-Tips.rst>`__.
