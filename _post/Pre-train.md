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

众所周知，该模型是在[Attention Is All You Need](https://arxiv.org/abs/1706.03762)中被提出的，详情可见我写的这篇[博客](论文解读/Attention%20Is%20All%20You%20Need.md)。
- BERT  
  使用了MLM，即随机掩盖掉一些单词，预训练任务就是利用这些被掩盖单词的上下文来预测该单词，显然，这里是双向的。公式上为$L(X)=\sum_{i-=1}^mlogP([Mask]_i=y_i|\tilde X;\Theta)$另外，还有一个NSP任务，但是后来证明，该任务并无实际作用。 
- GPT       
  GPT是第一个将transformer架构和自监督训练结合起来的模型，其使用的是自回归语言模型，即最大化所有单词在给定前述单词的条件概率，公式上为$L(X)=\sum_{i=1}^{n+1}logP(x_i|x_{i-k},....,x_{i-1};\Theta)$
- After GPT and BERT  
  - RoBERTa
    - 去除NSP任务
    - 更大的训练步数、batch size，更多的数据
    - 更长的训练句子
    - 动态改变mask的方式
  
  - AlBERT
    - 把输入的word embedding矩阵分解为更小的两个
    - transformer层之间共享参数
    - 用SOP代替NSP  
  <div align=center><img src="../image/pre-train/81aebdb583379636c328d5761b5188a.png" width="300"></div>

## 三 最新研究方向
### **Designing Effective Architectures**   

BERT之后的模型架构可分为两个设计思路
- Unified sequence modeling  
  NLP具有挑战性的一个基本问题就是其多样的下游任务，包括$Natural ~language~understanding,Open-ended~language~generation,Non-open-ended ~language ~generation$。但是观察发现，我们不必太过在意各种下游任务的区别，它们的界限是模糊不清的。换句话说，它们之间是可以进行转换的。基于该发现，后续的工作在需求使用一个PTM来统一不同任务的方式。这块的挑战是，encoder-decoder架构参数更多、NLU效果更差。
  - Combining Autoregressive and Autoencoding
Modeling  
    - XLNet：使用premutated language modeling将GPT-style
unidirectional generation和BERT-style bidirectional understanding结合了起来
    - MPNet：改进了XLNet在预训练是不知道序列长度，但是下游任务知道的问题
    - UniLM：使用multi-task training，即将包括unidirectional, bidirectional, and seq2seq objective连接进来训练
    - GLM：
  - Applying Generalized Encoder-Decoder   
    - MASS
    - T5
    - BART
  
- cognitive-inspired architecture  
  这里是介绍受人类感知系统启发的模型架构
  - Maintainable Working Memory   
  固定的窗口大小和指数级的空间复杂度限制了transformer在长文本上的理解和生成。人类的记忆机制为 *not only memorizes and organizes but also forgets*，LSTM便是一个典型的应用。
    - Transformer-XL:introduce segment-level recurrence and relative
positional encoding
    - CogQA:PTM+GNN
    - CogLTX:解决CogQA固定窗口的问题
  - Sustainable Long-Term Memory  
  Besides working memory for deciding and reasoning, the
long-term memory also plays a key role in recalling facts and experiences.
    - REALM:construct a sustainable external memory for Transformers
    - RAG:extends
the masked pre-training to autoregressive generation, which could be better than extractive question answering.

- optimizing BERT's architecture  
  改进掩码策略和更加为更难的掩码预测目标
  - Span-BERT:masking a continuous random-length span of tokens with a span boundary objective (SBO)
  - ERNIE:a whole entity is masked
  - NEZHA:
  - Whole Word Masking
  - ELECTRA：transform MLM
to a replace token detection (RTD) objective, in
which a generator will replace tokens in original
sequences and a discriminator will predict whether
a token is replaced


### **Utilizing Rich Contexts**
- Multilingual Pre-Training  
  虽然世界上的语言都不相同，但是它们可以表达一样的意思。实验证明，使用多语言进行训练，能够得到更好的性能。因此，学习multilingual representation可能是一个更好的方式。这里主要有两种学习方法：learn through parameter sharing和learn language-agnostic
constraints   
  - mBERT：pretrained with the multilingual masked language
modeling (MMLM) task using **non-parallel** multilingual Wikipedia corpora in 104 languages
  - XLM-R：XLM-R is pretrained with MMLM as the only task on
 Multimodal Pre-training **CC-100**，性能更好的原因是CC-100数据集更大
  - XLM：MMLM不能很好地利用parallel corpus，XLM利用**bilingual sentence pairs** to perform the translation language modeling
(**TLM**) task.This encourages models to align the representations of two languages together.
  - Unicoder：provides two novel pre-training tasks based on parallel corpora: cross-lingual word recovery (**CLWR**)
and cross-lingual paraphrase classification (**CLPC**).
  - ALM： automatically
**generates code-switched sequences** from parallel
sentences and performs MLM on it, which forces
models to make predictions based only on contexts
of other languages.
  - InfoXLM：analyzes MMLM and TLM from the perspective
of information theory, and encourages models to
distinguish aligned sentence pairs with misaligned
negative examples under the framework of **contrastive learning**
  - HICTL：extends
the idea of using contrastive learning to learn both
sentence-level and word-level cross-lingual representations.
  - ERNIE-M：proposes **back-translation masked language modeling**
(BTMLM), and expands the scale of parallel corpora through back-translation mechanisms.
  - mBART：extends **DAE**(replacing a span of tokens with a mask token
as well as permuting the order of tokens) to support multiple
languages by adding special symbols. It adds a language symbol both to the end of the encoder input
and the beginning of the decoder input. This enables models to know the languages to be encoded
and generated.
  - XNLG：proposes
the cross-lingual autoencoding (**XAE**) task. Different from DAE, the encoding input and the decoding
output of XAE are in different languages, which is
similar to machine translation.In addition, XNLG
optimizes parameters in a **two-stage manner**. It
trains the encoder with the **MLM and TLM tasks** in
the first stage. Then, it fixes the encoder and trains
the decoder with the **DAE and XAE tasks** in the
second stage. All parameters are well pre-trained
by this way, and the **gap** between pre-training with
MLM and fine-tuning with autoregressive decoding
is also filled.
- Multimodal Pre-training  
  一般来说，多模态工作大部分都是VLM，image and video belong to vision while text and speech belong to language.目前的多模态PTM主要关注三个方面：(1) improving model architecture, (2) utilizing more data, and (3) designing
better pre-training tasks   
目前大部分的工作都是基于visual-linguistic BERT的架构。而主要的挑战是如何将视觉和语言内容对齐到同一语义空间上，为了解决该问题，当前主要有两种设计架构：two-stream和single-stream。前者有ViLBERT和LXMERT；后者有VisualBERT、Unicoder-VL和B2T2。考虑到模型简单和参数效率，单流会是大部分人的选择。  
而在数据集方面，有*Conceptual Captions ,SBU Captions ,COCO , Flicker30K , GQA ,VQA and Visual Genome*   
UNITER就使用了上述的一些数据集来进行训练，充足的数据让它取得了不错的效果。ImageBERT进一步加入了一千万image-text pairs进行训练，VL-BERT加入了text-only corpora   
至于在预训练任务方面，有**MLM**, sentence-image alignment (**SIA**), masked region classification (**MRC**),
masked region feature regression (**MRFR**), and **directly incorporating downstream tasks**(LXMERT直接使用VQA)  
为了学习更细粒度的表示，UNITER提出了word-region alignment task in the way
of Optimal Transport, which
first finds a sparse matching between image regions
and words, and then minimizes the alignment distance.   
然而，上述的工作都忽略了**object tags**’ function as a kind of explicit bridges
between image regions and text tokens，为此，**Oscar**  proposes to concatenate
the object tags with original image-text pairs as anchors to learn the alignment between V&L modalities, and designs a new pre-training task for image-tag sequence-caption alignment judgment.   
并非直接设计预训练任务，**CLIP**和**WenLan** grasp the V&L
grounding ability in a simple and holistic regime。They encode images and captions into **holistic** visual and text representations rather than **separated**
region features and word embeddings, and then
only conduct an image-text retrieval task.这类整体对其方式的成功要归功于大规模的数据。   
上述模型可以用于V&L understanding和image captioning任务，但是无法用于image generation。**DALLE**展示了多模态PTM可以连接文本描述和图像生成。**CogView** further improves the
numerical precision and training stability by introducing sandwich transformer and sparse attention
mechanism     
最后，除了image-text PTMs，还有其他模态的，如VideoBERT、SpeechBERT


- Kownledge-enhanced Pre-training  
  **knowledge graphs**, **domain specific data** and **extra annotations of pre-training data**, is the outcome of human wisdom which can be a good prior to the modeling of statistics.(如果有应用需要可能看原文中提及的一些工作)
### **Improving Computational Efficiency**
  虽然PTM的趋势是参数量越来越大，准确率也相应提升。但是，同时训练模型所需的空间和计算开销也增加了。因此，下面将介绍三种提升计算效率的方法。
  - System-Level Optimization    
  系统级优化一般是model-agnostic，并且不会改变底层的训练算法，因此可以用于训练大规模的PTM
    - Single-Device Optimization    
  大量的空间消耗主要是因为redundant representation
of floating-point numbers。当前的深度学习系统主要基于FP32，但是模型的权值一般只处于一个有限的范围内，因此使用FP16已经并不会有太多的精度损失。   
话虽如此，但是在使用FP16进行训练可能会失败，原因是**floating-point truncation and overflow**。为了解决该问题，mixed-precision training methods应运而生，他的做法是preserve some
critical weights in FP32 to avoid the floating-point
overflow and use dynamic loss scaling operations
to get rid of the floating-point truncation。但是当模型参数初始化得不好时，该方法仍然会造成训练不稳定    
此外，the activation states saved for computing gradients也是冗余的，就比如实际上我们需要的是attention layers和linear layers，但是隐藏层我们也是需要大量内存进行存储的。基于此，Gradient checkpointing
methods have been used to
save memory by storing only a part of the activation
states after forward pass. The discarded activation
states are recomputed during the backward steps if
necessary.     
最后，近来也有尝试将模型参数和激活状态放到CPU而非GPU，如ZeRO-Offload，因为前者内存更大
    - Multi-Device Optimization   
  随着预训练模型的规模越来越大，分布式训练的思路也自然产生了，主要包括了data parallelism和model parallelism。在数据并行时，我们将一个大的batch划分到多个结点，在前向传播时，可以并行，在反向传播时，梯度需要汇集到一起。可以看到，这样会带来通信开销。    
  另一方面，模型的参数量往往十分庞大，使用一个GPU内存不足，因此我们可以考虑模型并行。具体做法就是，将模型参数划分到多个结点，而如reduce-scatter、all-gather的通信操作可以保证前行传播和反向传播的正确性。如**Megatron-LM**把self-attention heads和feed-forward layers分到了不同的GPU、**Mesh-Tensonflow**可以让用户把向量划分到不同的维度。   
  模型并行在前向传播和反向传播时都需要进行通信，而数据并行只需要在反向传播时进行通信，因此当内存足够时，后者会是更好的选择。   
  ZeRO通过在数据并行进程之间划分OGP模型状态而不是复制它们来消除数据并行进程之间的内存冗余，在训练过程中采用动态通信调度，保持了和数据并行基本一致的计算粒度和通信量，从而保持了计算/通信效率。  
  前面的模型并行是通过并行矩阵操作实现的，但是pipeline parallelism也是一种模型并行的方式。把每一个层划分到一个结点，一个结点计算结束之后把结果传到下一个结点，因此通信开销相对要少很多。相关工作有GPipe、TeraPipe。
  <div align=center><img src="../image/pre-train/3g453iuups.png" width="300"></div>
  <div align=center><img src="../image/pre-train/j8hraqv1fl.png" width="300"></div>    
    

  - Effective Pre-Training  
  预训练阶段的优化主要可以分为任务和架构。
    - Effective Training Methods    
  传统的预训练任务都比较地sample-inefficient，比如MLM，mask比例通常为15%，也就是说只有少部分信息可以学习到。基于此，ELECTRA改用了replaced token detection任务，相较于前者，这里模型利用的监督信息更多了，因为它需要判别每一个单词是否被替换了。    
  另外，MLM通常时随机mask的，训练过程会有点aimless和inefficient。因此，一些工作会选择基于单词的重要性或者在反向传播的梯度来加速训练。  
  pre-training dynamics通常也是次优化的。PTM需要大的batch size，但是会增加优化的难度。因此，他们提出了warmup strategy。另外，PTM一般由多个如transformer的基础结构堆叠而成。研究表明，some recent works study Transformer based models and claim that different layers can share similar self-attention patterns.因此，我们可以尝试先训练一个shallow model，然后将其进行复制，从而构建一个deep model。Some layers can also be **dropped** during training to reduce the complexity of back-propagation and
weight update (Zhang and He, 2020). In addition,
You et al. (2017) and You et al. (2020) find that
adaptively using **different learning rates** at different layers can also speed up convergence when the
batch size is large.
    - Effective Model Architectures
  - Model Compression

### **Theoretical Analysis**
