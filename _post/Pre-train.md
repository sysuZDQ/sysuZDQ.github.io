# Pre-train
本文基于综述论文[Pre-Trained Models: Past, Present and Future](https://arxiv.org/abs/2106.07139)对近下具有广泛研究前景的预训练模型进行梳理和学习。
## 一 什么是预训练模型
由于sophisticated pre-training objectives和huge model  parameters,  预训练模型能够数据中获取到知识，而这些所谓的知识就蕴藏在参数里面，并且能够应用于下游任务。  

目前来说，业界已经形成一种共识：adopt  PTMsas backbone for downstream tasks rather than learning  models  from  scratch。   

一般来说，提高预训练模型性能的方向有：designing  effective  architectures,  utilizing rich contexts,  improving com-putational efficiency, and conducting interpretation and theoretical analysis  

常见的深度神经网络有：CNNs、RNNs、GNNs和attention neural networks。但是他们有一个关键性的问题就是data hungry，如果没有足够的训练数据的话，它们非常容易产生overfit and have poor generalization ability的问题  

针对该问题，前人的想法是收集人工标注的高质量数据集，显然该做法是十分昂贵的。*how to train effective deep neural models for specific tasks with limited human-annotated data*一度成为当时的热门议题。  

受到人类学习机制的启发，transfer learning应运而生。其框架为：a pre-training phase to capture knowledge from one or more source tasks,and a fine-tuning stage to transfer the captured knowledge to target tasks  

与CV不太一样的是，NLP常常会利用自监督学习，即leverage intrinsic correla-tions in the text as supervision signals instead ofhuman supervision.   

the problem of vanishing or ex-ploding gradients一度是NLP中的痛点。为此，NLP采用了如Word2Vec、GloVe来捕捉单词的语义信息，但是它们一个单词只能用一个向量来表示，无法解决一次多义等问题  

transformers的出现让更加深层的神经网络成为可能，当然，increasing computationalpower boosted by the wide use of distributed com-puting devices and strategies也是PTM流行的一种重要诱因。  

PTM的基本问题有：不清楚隐层参数的意义以及巨大的计算资源
