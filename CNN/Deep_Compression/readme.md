# 性能提升方法
    1. 小模型 mobilenet
    2. 模型压缩：参数稀疏、量化、分解、去冗余。
    3. 高性能计算。

# 模型压缩

[DeepCompression-caffe](https://github.com/Ewenwan/DeepCompression-caffe)


## 为什么要压缩网络？
    做过深度学习的应该都知道，NN大法确实效果很赞，
    在各个领域轻松碾压传统算法，
    不过真正用到实际项目中却会有很大的问题：

    计算量非常巨大；
    模型特别吃内存；
    
    这两个原因，使得很难把NN大法应用到嵌入式系统中去，
    因为嵌入式系统资源有限，而NN模型动不动就好几百兆。
    所以，计算量和内存的问题是作者的motivation；

## 如何压缩？
      论文题目已经一句话概括了：
        Prunes the network：只保留一些重要的连接；
        Quantize the weights：通过权值量化来共享一些weights；
        Huffman coding：通过霍夫曼编码进一步压缩；
        
## 效果如何？
    Pruning：把连接数减少到原来的 1/13~1/9； 
    Quantization：每一个连接从原来的 32bits 减少到 5bits；

## 最终效果： 
    - 把AlextNet压缩了35倍，从 240MB，减小到 6.9MB； 
    - 把VGG-16压缩了49北，从 552MB 减小到 11.3MB； 
    - 计算速度是原来的3~4倍，能源消耗是原来的3~7倍；