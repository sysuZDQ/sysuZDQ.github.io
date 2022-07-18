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

## 二 预训练模型的背景知识
### Transfer Learning and Supervised Pre-Training
从定义来说，迁移学习是指：transfer learning aims to capture important knowledge from multiple source tasks and then apply the knowledge to a target task.  

显然，source tasks和target tasks的一致性是我们首先需要考虑的问题，pre-training methods往往是连接这两者的桥梁  

一般来说，有两种迁移方法：feature transfer  and  parameter  transfer  

从AlexNet到VGG和GoogleNet，网络变得越来越深，性能也相应的会越来越好，但会带来 vanishing or exploding gradients的问题。此外，model performance may soon meet a ceiling and then degrade rapidly with continually increasing network depths.  

ResNet通过正则化和残差层的方式，解决了这一问题。Based on the combination of effective model ResNet, informative dataset ImageNet, as well as mature knowledge transfer methods, a wave of pre-training models on labeled data emerges. CV界很多的做法都是用ResNet在ImageNet上进行预训练，之后应用到图像识别等下游任务上。而在NLP领域，CoVE是一个相应的工作。    

随着人们意识到无标注数据的价值，自监督应运而生。Self-supervised learning has been proposed to extract knowledge from large-scale unlabeled data by leveraging input data itself as supervision.其实自监督学习是无监督的一个分支，不同的是后者只是检测出数据的模式（如聚类），而前者更像监督学习。 

Compared to supervised pre-training working as the cornerstone of CV in the deep learning era, self-supervised pre-training allows for huge advances in the field of NLP.    

The recent stunning breakthroughs in PTMs are mainly towards NLP tasks, more specifically pre-trained language models.  

Using word embeddings as the input of neural models has almost become the common mode for NLP tasks.    

After Vaswani et al. (2017) propose Transformers to deal with sequential data, PTMs for NLP tasks have entered a new stage, because it is possible to train deeper language models compared to conventional CNNs and RNNs.   

With the recent advance of PTMs for NLP tasks,applying Transformer-based PTMs as the backbone of NLP tasks has become a standard procedure.之后，CV也尝试self-supervised learning + tansformer的方法，甚至有Transformer-based multimodal PTMs。   

The key to the success ofrecent PTMs is an integration of self-supervised learning and Transformer.其中最具代表性的莫过于autoregressive language modeling的GPT，以及autoencoding  language modeling的BERT，后续的PTMs都是两者的变种。  

### Transformer
Between neural layers,residual connection (He et al., 2016) and layer nor-malization (Ba et al., 2016) are employed, making it possible to train a deep Transformer.  


